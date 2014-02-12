CsvImport
=========

Get data from csv by column name 


##How to:
Import component by
`Yii::import('yopolis.components.CsvImport')` or in config.

You can get data in one cell by `$csv->get('Name')` or all data by `$csv->getAll()`.

For specify column names in returning array by `$csv->getAll()` use 
```
$csv->setAttributeMap(array(
  	'Name' => 'first_name',
));
```

##Example:
```
Yii::import('yopolis.components.CsvImport');

$csv = new CsvImport($_FILES['file']);
$csv->setAttributeMap(array(
  	'Name' => 'first_name',
  	'Currency' => 'currency',
  	'AboutUser' => 'about',
));

while ($csv->getLine() !== false)
{
    $model = new User();
    $model->setAttributes($csv->getAll());

    if ( !$model->save() )
    {
        throw new CHttpException(500);
    }
}
```
