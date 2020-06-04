## Installation symfony
- wget https://get.symfony.com/cli/installer -O - | bash

## Creation project
- symfony new --full my_project

#Symfony part config
## controller
-  bin/console make:controller

## Routes custom
- delete annotation from config/routes/annotations.yaml
- create folder :
    - src/Resources/config/routes
- create file { controlle_name }.yaml
- In the file { controlle_name }.yaml:



    route name :
        app_{ controller_name }_action
          path: { route/ }
          defaults:
            _controller: { controller_namespace }/{ controller_name }:action

- Load our route :
    - create file in src/Resources/config name : routes.yaml
    - In the file: \
    " app_{ controller_name }\
              &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;resource: "routes/{ controlle_name }.yaml" "
- Load our routes for each controller in symfony routes:
    - In the file config/routes/routes.yaml:\
    " app\
                  &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;resource: "../src/Resources/config/routes.yaml" "
## Template
- In public create folder assets/{ css, js, images } 
- In the file templates/base.html.twig :
    - add framework css, js example:
        - https://getbootstrap.com/
        - https://bulma.io/documentation/overview/start/
        
#Database part config

## Entities doctrine : create by yourself your entities *don't use cmd*
- Create entity depending controller data handle :
    - Create folder *src/Resources/config/doctrine*
- delete annotation
    - In file *config/packages/doctrine.yaml* edit field **type:annotation** by *type:yml*
    - In file *config/packages/doctrine.yaml* edit field **dir:'%kernel.project_dir%/src/Entity'** by **dir:'%kernel.project_dir%/src/Resources/config/doctrine'**  

- Create entity :
    - create class in src/Entity/{ entity_name }.php
        - In the file :
        
        
        <?php
        declare(strict_type=1;) 
        namespace App\Entity;
        class entity_name
        {
        /**@var int */
        private $id;
        ...\
        }
        
        
 - - create file src/Ressources/config/doctrine/{ entity_name }.orm.yml
    - add content :
    
    
    App\Entity\{ entity_name }:
        type: entity
        table: { entity_name }
        id:
            id:
                type: integer
                generator:
                    strategy: AUTO
        fields:
            { entity_attribut }:
                type: string
                unique: true/false
                column: { entity_attribut } "example businessDate => business_date"
- Run cmd to finish creation of your entity:  php bin/console make:entity --regenerate
- **!! Important !!**: Keep the return only for the *get functions* you should replace from all *set functions* :self by :void and delete the **return $this;**
- *You need to create entity interface to avoid and guarantee to you that whole your entity class is correct :
    - Create file src/Entity/{ entity_nameInterface }.php
    - In the file :
    
        
        <?php
        declare(strict_types=1);
        
        namespace App\Entity;
        interface entity_nameInterface {
            public function getId(): ?int;
            public function setId(int id): void;
        }
        
   - - Use your Interface *src/Entity/{ entity_nameInterface }.php* in *src/Entity/{ entity_name }.php* by Implement it !
        

#Controller part config
- Typage functions and variables 
    - Put Request $request as param of functions
    - return Response
    - import from HttpFoundation
- **If you keep autowire to true : means symfony manage all controllers** nothing to do all right
- **If you want to keep control on your controllers**
    - Create file src/Resources/config/services.yaml to centralised our services here by doing that :
    
    
        imports:
            - { resource: 'services/controller.yaml' }
    
   - - Create file src/Resources/config/services/controller.yaml  and put the next code :
        
        
        services:
            _default:
                tags: ['controller.service_arguments']
            app.controller.{ controller_name }:
                class: App\Controller\{ controller_classname }
                calls:
                    - [setContainer, ['@service_container']]
            
   - - In the file config/services.yaml delete all and put only the next code:
        
        
        imports:
            -{ resource: '../src/Resources/config/services.yaml' }
        services
            _defaults:
                autowire: false
                autoconfigure: false
    
        
  - - In the file { controlle_name }.yaml:
    
    
    
        route name :
            app_{ controller_name }_action
              path: { route/ }
              defaults:
                _controller: app.controller.{ controller_name }:action 
###Source
 - https://www.youtube.com/watch?v=C43tf5G7srw