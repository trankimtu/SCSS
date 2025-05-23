# 1. Variables (Store reusable values):

```
// _variables.
$primary-color: #007bff;
$spacing-unit: 8px;
$font-family: 'Arial', sans-serif;

.button {
    background: $primary-color;
    padding: $spacing-unit * 2;
    font-family: $font-family;
}
```
# 2. Nesting (Better organization):

```
.navbar {
    background: #333;
    padding: 16px;
    
    // Child elements
    ul {
        list-style: none;
        
        li {
            display: inline-block;
            margin-right: 20px;
            
            a {
                color: white;
                text-decoration: none;
                
                &:hover {  // & refers to parent selector
                    color: #ddd;
                }
            }
        }
    }
}
```

# 3. Mixins (Reusable style blocks):

```
@mixin flex-center {
    display: flex;
    justify-content: center;
    align-items: center;
}

@mixin button($bg-color, $text-color) {
    background: $bg-color;
    color: $text-color;
    padding: 10px 20px;
    border: none;
    border-radius: 4px;
}

.card {
    @include flex-center;
}

.primary-button {
    @include button(blue, white);
}

.secondary-button {
    @include button(gray, black);
}
```
# 4. Extensions (Share styles):

```
%base-box {
    padding: 20px;
    margin: 10px;
    border-radius: 4px;
}

.success-box {
    @extend %base-box;
    background: green;
}

.error-box {
    @extend %base-box;
    background: red;
}
```
# 5. Functions and Operations:

```
@function calculate-width($columns) {
    @return $columns * 100px;
}

.container {
    width: calculate-width(3);  // 300px
    padding: 20px + 10px;      // 30px
    margin: 50px / 2;          // 25px
}
```
# 6. Media Queries:

```
$tablet-width: 768px;
$desktop-width: 1024px;

@mixin tablet {
    @media (min-width: $tablet-width) {
        @content;
    }
}

.responsive-div {
    width: 100%;
    
    @include tablet {
        width: 50%;
    }
    
    @media (min-width: $desktop-width) {
        width: 33.33%;
    }
}
```
# 7. Import and Partials:

```
// _reset.```
* {
    margin: 0;
    padding: 0;
    box-sizing: border-box;
}

// main.```
@import 'reset';
@import 'variables';
@import 'mixins';
```
# 8. Color Functions:

```
.button {
    background: $primary-color;
    
    &:hover {
        background: darken($primary-color, 10%);
    }
    
    &:disabled {
        background: desaturate($primary-color, 50%);
    }
}
```
# 9. Lists and Maps:

```
$sizes: (
    'small': 8px,
    'medium': 16px,
    'large': 24px
);

.padding-small {
    padding: map-get($sizes, 'small');
}

$theme-colors: #ff0000, #00ff00, #0000ff;

@each $color in $theme-colors {
    .bg-#{$color} {
        background-color: $color;
    }
}
```
