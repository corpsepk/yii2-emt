yii2-emt Типограф Муравьёва
===============

Сайт типографа http://mdash.ru/

# Установка
```
composer require 'corpsepk/yii2-emt:^0.1'
```

# Использование
Модель
```php
use corpsepk\yii2emt\EMTypograph;

class ... extends \yii\db\ActiveRecord
{
    public function beforeSave($insert)
    {
        if (parent::beforeSave($insert)) {

            $EMTypograph = new EMTypograph();
            $EMTypograph->set_text($this->text);
            $EMTypograph->setup([
                'Text.paragraphs' => 'off', 
                'OptAlign.oa_oquote' => 'off'
                'Nobr.spaces_nobr_in_surname_abbr' => 'off',
                ...
            ]);
            $this->text = $EMTypograph->apply();

            return true;
        } else {
            return false;
        }
    }
}
```
