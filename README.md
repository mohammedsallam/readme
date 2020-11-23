* What does the application do?

CMS application management the content of your website,
like categories, articles, video categories, videos, photo galleries, 
website galleries, pages, newsletters, visitor message, users, and settings. 

- [Requirements](#requirements)
- [Installation](#installation)
- [Structure](#structure)
  - [notes about view:](#notes-about-view)
  - [Common functions](#common-functions)
- [DB Design](#db-design)
- [Test report](#test-report)

## Requirements 
* PHP version: 7.2.5 at least 
* Laravel framework version: 7
* Database type: Mysql 
* Mysql version: 8.0.18
* Linux server

## Installation

* Read installation: [Read this](installation.md)
  
## Structure

    Application based on laravel framework which use MVC pattern.
    Models: it's path falled into App directley.
    Views: it's path falled into resources\views.
    Controllers: it's path falled into App\Http\Controllers.
    Languages: it's path falled into  resources\lang.
  
### notes about view: 

CMS admin have master layouts that other modules layouts inhirit it,
and every module has 3 base files index to list data , 
grid to build grid for data, form to edit or create new data, 
and we us main javascript file like action.js that contains ajax request using xios object,
this file falled into path public/assets/admin/js
and about css files we use 2 main files for languages like style_en.css for english, styles.css for arabic,
that falled into path public/assets/admin/css,
we use too Form request for every modules which falled into path App\Http\Requests.

### Common functions
in common functions we use helpers that falled into path App\Helpers,
we use helper.php file which contains some function like currentLanguage() which get current application
language, getCurrentLocal() which specific current application local whether it's ar or en, languages() to get application
languages.
```php 
if (!function_exists('languages')){

    /**
     * Return list of languages from database
     * @return mixed
     */
    function languages()
    {
        $languages = Language::where('status', 1)->cursor();
        return $languages;
    }
}

if (!function_exists('currentLanguage')){

    /**
     * Return current language from database
     * @return mixed
     */
    function currentLanguage()
    {
        $languages = Language::where('status', 1)->where('local', LaravelLocalization::getCurrentLocale())->first();
        return $languages;
    }
}

if (!function_exists('getCurrentLocale')){

    /**
     * Return current locale from database
     * @return mixed
     */
    function getCurrentLocale()
    {
        $current = Language::where('status', 1)->where('local', LaravelLocalization::getCurrentLocale())->first()->local;
        return $current;
    }
}

```
we also use ImageHelper class to upload files and and resize images
```php 
/**
     * Helper to upload and resize Images
     * @param $image File to upload
     * @param int $width
     * @param int $height
     * @return string
     */
    public static function upload($image, $width= 200, $height= 200)
    {
        $newFileName = time().'.'.$image->extension();

        // Resize image and upload to Thumbnail path
        $destinationPath = public_path('/uploads/images/thumbs');
        $img = ImageResize::make($image->path());

        $img->resize($width, $height, function ($constraint) {
            $constraint->aspectRatio(); // to save the ratio
        })->save($destinationPath.'/'.$newFileName);

        // upload file to  Original path
        $destinationPath = public_path('/uploads/images');
        $image->move($destinationPath, $newFileName);

        return $newFileName;
    }
```

## DB Design 

* To read DB Design: [DB Design](design.md)
* DB Design file : [DB Design file](db_design.pdf)
* Other DB Design file : [Other DB Design file](db_design_1.pdf)
   
## Test report
In TDD we use phpunit as unit test for each units to application,
the unit testing falled into path tests directory which contains to directory,
Feature for test full feature for module and unit for test small unit for module,
and in common we use feature directory for test application, and every module have test file for it
