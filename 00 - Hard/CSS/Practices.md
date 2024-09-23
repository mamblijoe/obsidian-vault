# CSS

## Однонаправленная верстка

Отступы должны быть везде в одну сторону.

Блок не должен переживать об отступах о других блоках которые следуют за ними. Блок сам определяет нужный отступ от
предыдущего блока и не переживает о том что будет после него

## Принципы ОПП в CSS

* DRY
* CSS переменные
* Инкапсулируй то что может быть изменено (миксины, переменные и тд)

## Значения на основе шагов

```scss
$ui-step: 4px;

@mixin ui-space($direction, $size) {
  @if ($direction == top) {
    margin-top: $ui-step * $size;
  }
  @if ($direction == bottom) {
    margin-bottom: $ui-step * $size;
  }
  @if ($direction == left) {
    margin-left: $ui-step * $size;
  }
  @if ($direction == right) {
    margin-right: $ui-step * $size;
  }
}


.element {
  @include ui-space(top, 2);
  height: $ui-step * 10;
}
```

## Стандартизация

## Переиспользования стилей

### 2 компонента выглядят почти одинаково

Это один и тот же компонент?
> [!tip]
>* Темизация или параметры
>* Миксины с общими стилями и дописывание стилей которые отличаются

## Четкая система z-index

```scss
$ui-index-1: 1; // Для наползающих элементов в общем потоке
$ui-index-2: 2; // Для наползающих элементов в общем потоке
$ui-index-3: 3; // Для масок
$ui-index-4: 4; // Для сайдбаров
$ui-index-5: 5; //Для модалок
$ui-index-6: 6; // Для элементов, перекрывающих все

.modal {
  position: fixed;
  z-index: $ui-index-5;
}

.sidebar {
  position: fixed;
  z-index: $ui-index-4;
}
```

## Адаптив 

### Подходы desktop-first и mobile-first

### Назначение ховеров если пользователь исползует мышку

```scss
$mouse-device: '(hover: hover) and (pointer: fine)';

.button {
  background-color: red;
  &:hover {
    @media #{mouse-device} {
      background-color: black;
    }
  }
}
```

### Конфигурация медиа-запросов

```scss
$ui-media-mobile: 'screen and (max-width: 47.9625em)';
$ui-media-tablet: 'screen and (max-width: 63.9625em)';
$ui-mouse-device: '(hover: hover) and (pointer: fine)';
$ui-touch-device: '(hover: none) and (pointer: coarse)';
```

### Газетная метафора

* Отсупы / пустые строки между селесторами, импортами
* Логически связанные css правила группируются вместе и отделяют отступами / пустыми строками

### Никаких !important

### Закон  единого стиля

* Не дублировать селекторы