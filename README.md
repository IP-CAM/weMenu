## weMenu
======

Module for OpenCart

## Usage 
Since these menus are stored in the system settings, the menu can be displayed anywhere on the page, thereby not being limited to "locations"

Just paste the following code into any template such as `/catalog/view/theme/default/template/common/header.tpl`

```php
<?php if($we_menu_cache = $this->config->get('we_menu_cache')){ ?>
    <ul class="<?php echo $this->config->get('we_menu_class') ?>">
        <?php if(!empty($we_menu_cache)){ ?>
            <?php foreach($we_menu_cache as $item){
                $tpl = (strpos($_SERVER['REQUEST_URI'], $item['href']) !== false) && $_SERVER['REQUEST_URI'] != '/'  ? 'tpl_row_act' : 'tpl_row';
                echo str_replace('&', '&amp;', html_entity_decode($item[$tpl]));
                } ?>
        <?php } ?>
    </ul>
<?php } ?>
```
