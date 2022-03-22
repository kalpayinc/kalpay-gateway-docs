Usage
=====

.. _misenplace:

Installation
------------

Pour utiliser le *SuperSDK* la première chose à faire est de l'ajouter à votre page html.

Pour ajouter un script ou bibliothèque javascript tier, il y'a deux école :

* La manière synchrone

.. code-block:: html

   <!doctype html>
   <html>
   <head>
      <meta charset="utf-8">
      <title>KALPAY-Demo</title>
   </head>
   <body>
      <script src="kalpay-gateway-sdk-X.X.X.js"></script>
      <script>

      // Your code goes here.

      </script>
   </body>
   </html>

      
* La manière asynchrone 


.. code-block:: html

   <!doctype html>
   <html>
   <head>
      <meta charset="utf-8">
      <title>KALPAY-Demo</title>
   </head>
   <body>
      <script>
      (function(){
           window.superSDK_ready = window.superSDK_ready || [];
           var script = document.createElement('script');
           script.src = 'kalpay-gateway-sdk-X.X.X.js';
           script.async = true;
           var entry = document.getElementsByTagName('script')[0];
           entry.parentNode.insertBefore(script, entry);
       })();

       window.superSDK_Async = function() {

         // Your code goes here.

       }
      </script>
   </body>
   </html>


.. note::
    Nous recommandons la méthode `asynchrone`
    et d'inserer le code à la fin de votre code html pour une meilleure expérience utilisateur 



Commencer
---------

.. _initialisation:
1. Initialisation

Pour commencer l'expérience Kalpay, il faudra *obligatoirement* activer la passerelle grâce à la fonction ``superSDK.init()``.

.. autofunction:: superSDK.init

la fonction prend _deux_ paramètres : un ``identifiant`` et une ``fonction de callback``.

le paramètre ``identifiant`` doit être un objet du type : 

.. code-block:: json
   {
      accessKey: [ACCESS_KEY],
      secretKey: [SECRET_KEY]
   }

,
le paramètre ``fonction de callback`` sera du type : 

.. code-block:: javascript
   
   function(response){
      // Your code goes here.
   }


L'initialisation de la gateway dans une page html ressemblera à ceci :

.. code-block:: javascript
   
   superSDK.init({accessKey: [ACCESS_KEY], secretKey: [SECRET_KEY]},function(response){});


.. warning::
    le ``ACCESS_KEY`` et ``SECRET_KEY`` sont disponibles qu'après souscription à un compte **Kalpay Business**


.. _parametrage:
2. Paramètrage (Customisation)

Après *initialisation* ici :ref:`initialisation`, la seconde étape est de paramètrer votre passerelle.

Le paramètrage se fait grâce à la fonction ``superSDK.setup()``.

.. autofunction:: superSDK.setup

la fonction attend un ``objet de customisation``.

le paramètre ``objet de customisation`` ressemble à ceci : 

.. code-block:: javascript
   
   {
      store_name : [PAGE_NAME],
      triggerer: "render_zone",
      store_logo_url : [LOGO_URL],
      frame_color: [CUSTOM_COLOR]
   }

Le paramètrage de la gateway ressemblera à ceci :

.. code-block:: javascript
   
   superSDK.setup(
      {
         store_name : [PAGE_NAME],
         triggerer: "render_zone",
         store_logo_url : [LOGO_URL],
         frame_color: [CUSTOM_COLOR]
      }
   );

.. note::
    ``LOGO_URL`` n'est pas obligatoire et doit être un lien externe (http://lien_vers_image)
    ``CUSTOM_COLOR`` est un code hexadecimal (#03fc7b)

Exemple
-------

Voici un exemple de code *javascript* intégrant la Gateway de Kalpay

.. code-block:: javascript
   <script>
       (function(){
           window.superSDK_ready = window.superSDK_ready || [];
           var script = document.createElement('script');
           script.src = 'kalpay-gateway-sdk-1.0.4.js';
           script.async = true;
           var entry = document.getElementsByTagName('script')[0];
           entry.parentNode.insertBefore(script, entry);
       })();
 
       window.superSDK_Async = function() {
          
           superSDK.init({accessKey: [ACCESS_KEY], secretKey: [SECRET_KEY]},function(response){});
           superSDK.setup({
               store_name : [PAGE_NAME],
               triggerer: "render_zone",
               store_logo_url : [LOGO_URL],
               frame_color: [CUSTOM_COLOR]
           });
           superSDK.addItem({
               name : [ITEM_NAME],
               quantity: [ITEM_QUANTITY],
               unit_price : [ITEM_PRICE],
               item_photo : [ITEM_PHOTO_URL]
           });
           // define superSDK navigation
           superSDK.setNavigation({
               success_url : [TRANSACTION_SUCCESS_PAGE_URL],
               failed_url : [TRANSACTION_FAILED_PAGE_URL],
               back_url : window.location.href
           })
       }
   </script>

Pour afficher la gateway, inserer le code suivant dans un code *html* 

.. code-block:: html
   <button onclick="superSDK.proceed(this)">
      Payer avec Kalpay
   </button>

.. note::
   La méthode ``superSDK.proceed()`` lance la gateway avec les données précédemments renseignées.

