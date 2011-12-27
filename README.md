## djangoCMS/Shop Configurable Products Extension

This simple extension provides some plugins to display things about your
[django-shop configurable products](https://bitbucket.org/zeus/django-shop-configurableproduct).


## Requirements

* django-shop
* django-cms
* configurable-products
* And all the requirements the above three projects depend on.


## Installation

1. make sure you are using a python virtual environment
    virtualenv ~/Dev/virtualenv/projectname
    . ~/Dev/virtualenv/projectname/bin/activate
    cd ~/Dev/projects/projectname/

2. install it from pypi

    pip install djangocms-plugin-menu

3. or, install it from github

    pip install git+https://github.com/airtonix/djangocms-plugin-menu


## Override Template

Choosing a template in the administration interface means that you
populate the following two relative paths (to any of your app template dirs)

* cms/plugins/configurable_product/product-types
* cms/plugins/configurable_product/product-list


Any .html file that doesn't contain the word 'base' will be presented in
the template selector combo dropdown in the admin interface.


### Customising Templates

Templates in all groups are provided the context :

a CMSPlugin has many useful attributes for you to use, the main one
is `plugin.instance` a reference to the settings model.

>     plugin' :
>         An instance of CMSPlugin, which itself provides reference to either
>         of the settings models as outlined below.

#### base.html

base.html in each plugin subdir is used to load the selected template
chosen in the administration interface.


#### ./product-types/*.html

templates here are provided the context :

>     plugin.instance
>          categories
>               Chosen categories for this instance,
>
>          show_category_icon
>               For when configurable_product.ProductType stores an image.
>
>          hide_empty_categories
>               Self explanitory, effected in the cms_plugin.
>
>          template
>               Chosen template.
>
>     Types
>        A list of configurable_product.ProductType(s)


#### ./product-list/*.html

templates here are provided the context :


>     plugin.instance
>          categories
>               Chosen categories for this instance,
>
>          hide_empty_categories
>               Self explanitory, effected in the cms_plugin.
>
>          template
>               Chosen template.
>
>          filter_product_attributes
>               Comma separated list of CProductField names on which to
>               effect a filter action of either Filter, or Exclude.
>
>          filter_action
>               The action to take on the filter attributes listed above.
>
>     Products
>        A list of configurable_product.CProduct(s)



## Contributions

anyone is free to contribute, simply submit a merge request at
github : http://github.com/airtonix/djangocms-plugin-configurableproduct


## Todo

provide option to manipulate menu choices:

* Refine the product filter.
* Provide better default templates.
* Allow selecting/use of snippets for menu templates?
