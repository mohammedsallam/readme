### Application structure:
* Application based on laravel framework which use MVC pattern.
* Models: it's path falled into `App` directly.
* Views: it's path falled into `resources\views`.
* Controllers: it's path falled into `App\Http\Controllers`.
* Languages: it's path falled into  `resources\lang`.
  
### Notes about view: 

* CMS admin have master layouts that other modules layouts inherit it.
* Every module has 3 base files index to list data, 
grid to build grid for data, form to edit or create new data.
* About javascript we us main javascript file like `action.js` that contains ajax request using axios object,
this file falled into path `public/assets/admin/js`.
* About css files we use 2 main files for languages like `style_en.css` for english, `styles.css` for arabic,
that falled into path `public/assets/admin/css`.
* We use too Form request for every modules which falled into path `App\Http\Requests`.

### Common functions
* In common functions we use helpers that falled into path `App\Helpers` that we can call up it in every where in application.
* We use `helper.php` file which contains some function like `currentLanguage()` which get current application
language, `getCurrentLocal()` which specific current application local whether it's `ar` or `en`, `languages()` to get application
languages.
* We also use ImageHelper class to upload files and resize images.
