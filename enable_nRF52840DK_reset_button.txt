\ This program will correctly enable the reset button on the nRF52840-DK.

HEX
\ 4001E000 CONSTANT NVMC
4001E504 CONSTANT NVMC_CONFIG
4001E514 CONSTANT NVMC_ERASEUICR
: ENABLE_NVMC_WRITE 1 NVMC_CONFIG ! ;
: DISABLE_NVMC_WRITE 0 NVMC_CONFIG ! ;
: ENABLE_NVMC_ERASE 2 NVMC_CONFIG ! ;
: DISABLE_NVMC_ERASE 0 NVMC_CONFIG ! ;
: ERASE_UICR ENABLE_NVMC_ERASE 1 NVMC_ERASEUICR ! DISABLE_NVMC_ERASE ;

\ 10001000 CONSTANT UICR \ base address for UICR registers
10001200 CONSTANT PSELRESET[0]
10001204 CONSTANT PSELRESET[1]

\ Note: PSELRESET[0] must exactly match PSELRESET[1] for reset pin to be enabled
: SET_PSELRESET[0]  PSELRESET[0] ! ;  \ (desired_reset_pin --  ) enable desired_reset_pin as reset pin
: SET_PSELRESET[1]  PSELRESET[1] ! ;  \ (desired_reset_pin --  ) enable desired_reset_pin as reset pin
: ENABLE_RESET_PIN DUP SET_PSELRESET[0] SET_PSELRESET[1] ; \ (desired_reset_pin --  ) enable desired_reset_pin as reset pin

\ (desired_reset_pin --  )  This one word does it all
\ Note: Change only goes into effect after either a reset or a power-cycle, 
\ so this resets for immediate effect
: MAKE_RESET_PIN ERASE_UICR ENABLE_NVMC_WRITE ENABLE_RESET_PIN DISABLE_NVMC_WRITE RESET ;

\ On the nRF52840-DK, pin P0.18 is the reset button
decimal
18 MAKE_RESET_PIN
\ 
\ ASSERTION: reset pin is now working on the nRF52840-DK
\ Note: GPIO pin P0.18 does *not* need to be set as an input pin for the reset pin to work
\ Note: Change has been made in non-volitile memory, so the reset pin is now permanent 
\ and will work indefinitely unless it is later intentionally set to something else or a bulk erase
\ is performed.