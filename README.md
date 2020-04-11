# Настройка кнопок трекбола Kensington SlimBlade Trackball для Ubuntu

1. 
Ввести в консоль xinput для определения id устройства
xinput test ID для определения номера клавиш
xinput get-button-map ID - получаем карту клавиш
xinput --set-button-map ID 1 8 3 4 5 6 7 2 - применяет карту клавиш, действует на сеанс до перезагрузки

2.
Создаем файл по адреса **/usr/share/X11/xorg.conf.d/10-evdev.conf**

3. Добавляем в файл
```
# Kensington Slimblade Settings

Section "InputClass"
Identifier "Kensington Slimblade Trackball"
MatchProduct "Kensington Slimblade Trackball"
MatchIsPointer "on"
MatchDevicePath "/dev/input/event*"
Driver "evdev"

Option "ButtonMapping" "1 8 3 4 5 6 7 2"

EndSection
```

Button's numbers
```
2 - middle-click
8 - backward
9 - forward 
```
Use **xev** tool to figure out the number of each button on your mouse.

And restart Service or PC

### For changing scroll speed
```
sudo apt install imwheel
cd /etc/X11/imwhell
sudo vim imwheelrc
imwheel --kill --buttons "4 5"
```

