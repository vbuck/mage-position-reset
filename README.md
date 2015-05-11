# Category Position Reset
A bookmarklet to reset category product positioning values.
---
### How to Use:
 1. Visit the bookmarklet page.
 2. Drag the bookmarklet into your bookmarks bar.
 3. Visit the desired product category.
 4. Click the bookmark.
 5. Enjoy.

### Alternate Method A:
Paste the following script into your browser console:
```javascript
javascript:(function(){$$('#catalog_category_products_table input[name="position"]').each(function(e){e.value='0'})})();
```

### Alternate Method B:
Do it server-side a la PHP:
```php
Mage::app()->setCurrentStore(Mage_Core_Model_App::ADMIN_STORE_ID);

$categoryId  = 22;
$newPosition = 100;

$category = Mage::getModel('catalog/category')
  ->setStoreId(Mage_Core_Model_App::ADMIN_STORE_ID)
  ->load($categoryId);
$products = $category->getProductsPosition();

foreach ($products as $id => $value){
    $products[$id] = $newPosition;
}

$category->setPostedProducts($products);

$category->save();
```
Thanks (Marius)[http://magento.stackexchange.com/a/11161]!
