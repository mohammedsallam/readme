## DB design 
* In database Design we depend on tow tables for each module.
* First table(main table) and second table which contains translation text for module.
* EXAMPLE: `pages` as main table [`id`, `image`], and `page_descriptions` as translation table [`title`, `slug`, `meta`, `keywords`, `description`, `page_id`, `language_id`].
* DB structure pdf [file](db_design.pdf).
* DB relation png [file](db_design.png).
