#Creation of forms

##Dependances
- Form (form builder)
>composer require form

##CRUD
>php bin/console doctrine:generate :crud app:City

##show form
>$form->createView()
- in your view :
>{{ form(myForm) }}

##Save form date
- inject EntityManagerInterface in your controller then use it :
>$em->persist($myObj);
>$em->flush();



###Sources
- https://www.youtube.com/watch?v=Q8qrZzPTk-o