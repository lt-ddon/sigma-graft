[🇬🇧 English](README.en.md)
# Wstęp
Próba naprawy obiektywu Sigma AF-Kappa z bagnetem Sony A-Mount poprzez podmianę wadliwego układu ASIC na mikrokontroler Attiny.
Implementacja nie jest w pełni kompatybilna z protokołem nasłuchiwanym z obiektywu przez ograniczenia w procesie reverse-engineeringu.
Jednak sposób ten przywraca obiektyw z całkowitego uszkodzenia do stanu używalności.
Użyta w kodzie źródłowym ramka danych pochodzi z obiektywu o parametrach zbliżonych do Sigma AF-Kappa, nie jest w pełni dopasowana.
# Wykonanie
Program został przetestowany przy użyciu Attiny24A(mikrokontroler powinien mieć niewielkie rozmiary, oraz posiadać min. 7 pinów GPIO).
Mikrokontroler należy zaprogramować, a następnie zamontować w miejsce z zaizolowanymi padami po demontażu starego układu.
Do Attiny24A należy podłączyć ścieżki stykowe tubusu oraz piny bagnetu wg poniższej listy:
```
ATTINY24A       - SIGMA
- Pin 14 (VCC)  - 5V (Bagnet)
- Pin 13 (PA0)  - Ścieżka stykowa "0"
- Pin 12 (PA1)  - Ścieżka "1"
- Pin 11 (PA2)  - Ścieżka "2"
- Pin 10 (PA3)  - Ścieżka "3"
- Pin 9  (SCK)  - CLK  (Bagnet)
- Pin 8  (MISO) - MOSI (Bagnet)
- Pin 5  (INT0) - SS   (Bagnet)
- Pin 4  (RST)  - przez rezystor 10k do 5V
- Pin 1  (GND)  - Masa
```
Warto zmierzyć połączenia ścieżek stykowych tubusu testerem ciągłości, aby upewnić się że piny mikrokontrolera są podłączone do odpowiednio ponumerowanych ścieżek.
Poniżej zdjęcie przykładowego wykonania mikrokontrolera Attiny24A:
![Zdjęcie](circuitry.png)

# Kompilacja
Kod został napisany w avrgcc, ale można go skompilować w Arduino IDE. W tym celu można posłużyć się [SpenceKonde/ATTinyCore](https://github.com/SpenceKonde/ATTinyCore).
