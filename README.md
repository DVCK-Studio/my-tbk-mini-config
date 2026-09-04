# TBK Mini ZMK firmware

Конфигурация ZMK для TBK Mini на двух платах Nice Nano v2 (nRF52840).

## Сборка

После push в GitHub Actions автоматически собираются прошивки для левой и правой половин. Готовые `.uf2` находятся в артефактах workflow `Build ZMK firmware`.

Для локальной сборки нужен ZMK и west:

```sh
west init -l config
west update
west build -s zmk/app -b nice_nano_v2 -- -DSHIELD=tbk_mini_left
west build -s zmk/app -b nice_nano_v2 -- -DSHIELD=tbk_mini_right
```

Левая половина является central и подключается к Bluetooth-хосту. Правую половину прошейте правой прошивкой, затем подключите обе платы между собой через провод split-соединения.

## Настройка раскладки

Редактируйте `config/tbk_mini.keymap`. В нём пять слоёв: основной, lower, raise, adjust и navigation. После изменения раскладки повторно запустите workflow.