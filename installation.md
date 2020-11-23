* To install project follow next steps.
    
    1- Install composer.
    
        composer install 
   
    2- Create .env file.
    
        cp .env.example .env 
    
    3- Make your DB, and set the configuration in the env file.
    
    4- Generate key for application.
    
        php artisan key:generate 
    
    5- Migrate Database.
    
        php artisan migrate 
        
    6- Seed database.
   
        php artisan db:seed