

## Mautic API in Laravel/Lumen.

#####Esse pacote é uma atualização e algumas motificações do pacote do Prince Ali Khan

https://github.com/princealikhan/laravel-mautic-api
## Mautic Configurações
A API deve estar ativada no Mautic. No Mautic, vá para a página Configuração (localizada no menu Configurações) e, em Configurações da API, ative a API do Mautic. Você também pode escolher qual protocolo OAuth2 usar aqui. Depois de salvar a configuração, acesse a página Credenciais da API (localizada no menu Configurações) e crie um novo cliente. Insira o URI de retorno / retorno de chamada para o qual a solicitação será enviada. Clique em Aplicar e copie o ID do cliente e o Segredo do cliente para o aplicativo que usará a API.

## Instalação


```sh
composer require EduardoVargas/mautic
```

 `php artisan vendor:publish`  

## Configuration
You need to add your `client id`, `client secret` and  `callback url`  in `mautic.php` file that is found in your applications `config` directory.

## Authorization
This Library only support OAuth2 Authorization
you must need to create a OAuth2 client in order to use api.

## Registering Application
In order to register you application with mautic ping this url this is one time registration.
```url
http://your-app/mautic/application/register
```


# Usage
Add Mautic Facade in your controller.
```php
use Mautic;
```
#### Send a request to mautic ( Example )
Create a new contact in mautic.
```php
$params = array(
    'firstname' => 'Eduardo',
    'lastname'=> 'Ali Khan',
    'email' => 'eduardo.a.vargas@gmail.com'
);

Mautic::request('POST','contacts/new',$params);
```
Get List of all contacts
```php
Mautic::request('GET','contacts');
```
Get a unique contact
```php
Mautic::request('GET','contacts/1');
//where 1 is unique id for a contact.
```

Delete a contact
```php
Mautic::request('Delete','contacts/1/delete');
```
##### And many more endpoints support by mautic.
### List of Endpoints supported by Mautic.

#### Contacts 
```json
[
    "contacts",
    "contacts/{id}",
    "contacts/list/fields",
    "contacts/list/owners",
    "contacts/new",
    "contacts/{id}/edit",
    "contacts/{id}/delete",
    "contacts/{id}/notes",
    "contacts/{id}/segments",
    "contacts/{id}/campaigns"
]
```

#### Assets 
```json
[
    "assets",
    "assets/{id}"
]
```

#### Campaigns 
```json
[
    "campaigns",
    "campaigns/{id}",
    "campaigns/contact/{id}/add/{leadId}",
    "campaigns/contact/{id}/remove/{leadId}"
]
```

#### Data 
```json
[
    "data",
    "data/{type}",
]
```
#### Emails 
```json
[
    "emails",
    "emails/{id}",
    "emails/{id}/send",
    "emails/{id}/send/lead/{leadId}"
]
```

#### Forms 
```json
[
    "forms",
    "forms/{id}"
]
```
#### Pages 
```json
[
    "pages",
    "pages/{id}"
]
```
#### Points 
```json
[
    "points",
    "points/{id}",
    "points/triggers",
    "points/triggers/{id}"
]
```
#### Reports 
```json
[
    "reports",
    "reports/{id}"
]
```
#### Segments 
```json
[
    "segments",
    "segments/contact/{id}/add/{leadId}",
    "segments/contact/{id}/remove/{leadId}"
]
```
#### Users 
```json
[
    "roles",
    "roles/{id}",
    "users",
    "users/{id}",
    "users/list/roles",
    "users/self",
    "users/{id}/permissioncheck",
]
```

Please refer to [Documentation](https://developer.mautic.org).
for all customizable parameters.
