
LESS vs SASS:

@var: -1px;
.main { margin: 3px @var -@var -(@var + 5) } >> .main { margin: 3px -1px 1px -4px; }
$var: -1px;
.main { margin: 3px $var (-$var) (-$var - 5) } >> .main { margin: 3px -1px 1px -4px; }

0.  symbol_check: ([^0-9_a-zA-Z`~!@#$%\^&\(\)\{\}\[\]\+\-\*\\\|/=<>\.,:;'"\?\t \r\n])
    
        \) {2,}\-?\(
        \) {2,}\-?\d
        \) {2,}\-?\w
        \d {2,}\-?\(
        \w {2,}\-?\(
        \d {2,}\-?\d
        \d {2,}\-?\w
        \w {2,}\-?\d
        \w {2,}\-?\w
        
        \) {2,}\-?@\w+
        \d {2,}\-?@\w+
        \w {2,}\-?@\w+

1.  less2sass ./less

2.  @import 'default.scss' >> 'default'

3.  convert: ±$w+ / ±($w+) to ±#{$w+}

        /// Some-experiments-of-RegEx!
        : (\-?\$\w+)(\s*[;!\+\-\*\\%/\)]) >> :_\1\2 /** exclude_single_variables */
        (:|,|\d|\w|\)|\})\s+(\-?\$\w+) >> \1 #{\2}
        
        : (\-?\(\s*[^a-zA-Z].*?\))(\s*[;!]) >> :_\1\2
        (:|,|\d|\w|\)|\})\s+(\-?\() >> \1 #{\2}
        
        Simple: ([:]\s+\-\$\w+\s+)|([^:]\s+\-\$\w+)

4.  mixins:
    addScrollbars
    loadOutlineIcons
    loadBrandIcons
    loadFonts

5.  functions:
    @function unit-less($value, $unit)
    {
        $currentUnit: unit($value);
        $strippedValue: $value / ($value * 0 + 1);
        
        @if $unit == em {
            @return $strippedValue + 0em;
        }
        @else
        if $unit == rem {
            @return $strippedValue + 0rem;
        }
        
        @error "Can't convert '#{$value}' to unit '#{$unit}'!";
    }

6.  calcs:
C:\Users\User\Desktop\semantic\scss_\_dropdown.scss (10 hits)
    Line 204: $selectionItemHeight: calc(($selectionItemVerticalPadding * 2) + $itemLineHeight + $selectedBorderEMWidth); ///!
    Line 205: $selectionMobileMaxMenuHeight: calc($selectionItemHeight * $selectionMobileMaxItems); ///!
    Line 206: $selectionTabletMaxMenuHeight: calc($selectionItemHeight * $selectionTabletMaxItems); ///!
    Line 207: $selectionComputerMaxMenuHeight: calc($selectionItemHeight * $selectionComputerMaxItems); ///!
    Line 208: $selectionWidescreenMaxMenuHeight: calc($selectionItemHeight * $selectionWidescreenMaxItems); ///!
    Line 354: $scrollingItemHeight: calc(($itemVerticalPadding * 2) + $itemLineHeight + $scrollingBorderEMWidth); ///!
    Line 355: $scrollingMobileMaxMenuHeight: calc($scrollingItemHeight * $scrollingMobileMaxItems); ///!
    Line 356: $scrollingTabletMaxMenuHeight: calc($scrollingItemHeight * $scrollingTabletMaxItems); ///!
    Line 357: $scrollingComputerMaxMenuHeight: calc($scrollingItemHeight * $scrollingComputerMaxItems); ///!
    Line 358: $scrollingWidescreenMaxMenuHeight: calc($scrollingItemHeight * $selectionWidescreenMaxItems); ///!
C:\Users\User\Desktop\semantic\scss_\_list.scss (1 hit)
    Line 190: $horizontalBulletSpacing: calc($bulletDistance + 0.5em); ///!
C:\Users\User\Desktop\semantic\scss_\_loader.scss (8 hits)
    Line 328:   padding-top: calc($mini + $textDistance); ///!
    Line 332:   padding-top: calc($tiny + $textDistance); ///!
    Line 336:   padding-top: calc($small + $textDistance); ///!
    Line 340:   padding-top: calc($medium + $textDistance); ///!
    Line 344:   padding-top: calc($large + $textDistance); ///!
    Line 348:   padding-top: calc($big + $textDistance); ///!
    Line 352:   padding-top: calc($huge + $textDistance); ///!
    Line 356:   padding-top: calc($massive + $textDistance); ///!
C:\Users\User\Desktop\semantic\scss_\_modal.scss (1 hit)
    Line 84: $innerCloseTop: calc($headerVerticalPadding - $closeHitBoxOffset + ($lineHeight - 1em)); ///!
C:\Users\User\Desktop\semantic\scss_\_rail.scss (1 hit)
    Line 52: $dividingWidth: calc($width + $splitDividingDistance); ///!
