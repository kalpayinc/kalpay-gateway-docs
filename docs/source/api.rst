API
===

superSDK.init
-------------

la méthode ``init(credential, callback_fn)`` active la gateway grâce aux paramètres d'authentification, vérifie l'identité du compte associé et s'assure de son authenticité.


+------------------------+-----------------------------------------------------------------------------------+
| Paramètres             | détails                                                                           |
+========================+===================================================================================+
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

.. code-block:: javascript

   function(response){
   
   }


superSDK.setup
--------------

la méthode ``setup(custom_settings)`` permet de définir les éléments de customisation de la gateway.

+--------------------------+------------------------+
| Paramètre                | détails                |
+==========================+========================+
| custom_settings (Object) | objet de customisation |
+--------------------------+------------------------+

custom_settings (obligatoire)
+++++++++++++++++++++++++++++

.. code-block:: javascript

   {
      store_name : [PAGE_NAME], // le nom du site ou page, utilisé pour la facturation
      triggerer: "render_zone",
      store_logo_url : [LOGO_URL], // le logo du site ou page
      frame_color: [CUSTOM_COLOR] // la couleur du ui (hex) de la gateway : bouton, labels, etc..
   }

superSDK.addItem
----------------

la méthode ``addItem(item)`` permet d'ajouter un article à la liste des articles à afficher dans la gateway pour paiement.

+---------------+---------------------+
| Paramètre     | détails             |
+===============+=====================+
| item (Object) | article à facturer  |
+---------------+---------------------+

item (obligatoire)
++++++++++++++++++

.. code-block:: javascript

   {
      name : [ITEM_NAME], // nom de l'article
      quantity: [ITEM_QUANTITY], // quantité de l'article
      unit_price : [ITEM_PRICE], // prix unitaire de l'article
      item_photo : [ITEM_PHOTO_URL] // photo de l'article
   }


superSDK.setNavigation
----------------------

la méthode ``setNavigation(navigation_settings)`` permet de définir la politique de redirections de la gateway à la fin de la transaction.
Les redirections se feront ``3s`` après fin de la transaction.

+------------------------------+---------------------------------------------------+
| Paramètre                    | détails                                           |
+==============================+===================================================+
| navigation_settings (Object) | urls à suivre pour chaque scenari de transactions |
+------------------------------+---------------------------------------------------+

navigation_settings
+++++++++++++++++++

.. code-block:: javascript

   {
      success_url : [TRANSACTION_SUCCESS_PAGE_URL], // url à laquelle se rediriger au succès de la transaction
      failed_url : [TRANSACTION_FAILED_PAGE_URL], // url à laquelle se rediriger à l'échec de la transaction
      back_url : window.location.href // url de retour après annulation
   }


superSDK.setOperators
---------------------

la méthode ``setOperators(operators_list)`` permet de définir la liste des opérateurs de paiement acceptés dans la gateway.
La liste des opérateurs est composée du code des opérateurs, exemple : "OrangeMoney","EMoney"

+--------------------------------+------------------------------------------------------------------+
| Paramètre                      | détails                                                          |
+================================+==================================================================+
| operators_list (Array<String>) | liste des opérateurs de paiement à afficher dans votre gateway   |
+--------------------------------+------------------------------------------------------------------+

operators_list
+++++++++++++++

.. code-block:: javascript

   const operators_list = ["OrangeMoney","EMoney","FreeMoney"]


.. autosummary::
   :toctree: generated

   lumache
