# `convertWebDirectorySchemaToMarkup()`
Converts a web directory schema (expressed as JSON, a JS Object or as a PHP Array) into HTML Markup.

## Javascript: convertWebDirectorySchemaToMarkup
```js

```

_____

## PHP: convertWebDirectorySchemaToMarkup
```php

function convertWebDirectorySchemaToMarkup($webDirectory) {
  
  $markup = '';
  $filesMarkup = '';

  $arrayKeys = array_keys($webDirectory);

  if (count(array_keys($webDirectory)) >  0) {

    $markup .= '<ul class="webDirectory">';

    foreach($arrayKeys as $arrayKey) {

      if ($arrayKey === 'Files') {
      
        $files = $webDirectory['Files'];

        if (count($files) > 0) {

          $filesMarkup .= '<li class="webDirectoryFile">'. implode('</li><li class="webDirectoryFile">', $files).'</li>';
        }
      }

      else {

        $markup .= '<li class="webDirectoryFolder">';
        $markup .= $arrayKey;
        $markup .= convertPHPArrayToMarkup($webDirectory[$arrayKey]);
        $markup .= '</li>';
      }
    }

    $markup .= $filesMarkup;
    $markup .= '</ul>';
  }

  return $markup;
}

```