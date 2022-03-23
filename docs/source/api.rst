API
===

superSDK.init
-------------

la méthode ``init(credential, callback_fn)`` active la gateway grâce aux paramètres d'authentification, vérifie l'identité du compte associé et s'assure de son authenticité.


+------------------------+-----------------------------------------------------------------------------------+
| Paramètres             | détails                                                                           |
+========================+===================================================================================+
|                        |                                                                                   |
+------------------------+-----------------------------------------------------------------------------------+
| credential (Object)    | objet d'authentification                                                          |
+------------------------+-----------------------------------------------------------------------------------+
| callback_fn (function) | fonction de callback pour capter à la réponse de l'initialisation de la gateway   |
+------------------------+-----------------------------------------------------------------------------------+

credential (obligatoire)
++++++++++

.. code-block:: javascript

   {
      accessKey: [ACCESS_KEY],
      secretKey: [SECRET_KEY]
   }

callback_fn
++++++++++

.. highlight:: javascript

   function(response){
   
   }


superSDK.setup
--------------


superSDK.addItem
----------------


superSDK.setNavigation
----------------------

superSDK.setOperators
---------------------

.. autosummary::
   :toctree: generated

   lumache
