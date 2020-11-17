# Ivory register bindings for AVR Atmega328p

[![Build Status](https://travis-ci.org/erdeszt/ivory-avr-atmega328p-registers.svg?branch=master)](https://travis-ci.org/erdeszt/ivory-avr-atmega328p-registers)

Generated with: https://github.com/erdeszt/ivory-avr-generator

Example:

```haskell
import Ivory.Language
import Ivory.HW
import Ivory.Avr.Atmega328p.Registers

-- Blink the onboard led (pin13, ddrb 5) on the Arduino Uno/Nano as fast as possible
rapidBlink :: Def ('[] :-> ())
rapidBlink = proc "rapidBlink" $ body $ do
    setReg regBitsDDRB (setBit ddb5)
    forever $ do
        setReg regBitsPORTB (setBit portb5)
        setReg regBitsPORTB (clearBit portb5)
```
