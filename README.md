Coco! Multi file Uploader Widget
================================

by: Christian Salazar. christiansalazarh@gmail.com	@yiienespanol, oct. 2012.

[BSD Licence](http://opensource.org/licenses/bsd-license.php)"http://opensource.org/licenses/bsd-license.php"

(Español & English)

1.	Single & Multi File Uploads via Ajax-jQuery
1.	Drag & Drop.


[EN]
'Coco' is a widget for yii framework designed to handle File Uploads (Single and Multiple). Is designed using Ajax-jQuery and a well formed Architecture based on MVC (and UML).  Using 'coco' is very simple, at first place you setup a fixed action in any controller, this action serves for all every coco-widgets in your application. At second place you insert the widget in your form, all uploaded files will be stored in the path provided by 'uploadDir' widget attribute. Very simple and usefull. Please enjoy it.
'
Coco takes its functionality from a very nice PHP library located at valums repository in github, all licences are explicit in coco related to Valums work.


[ES]
'Coco' es un widget (aparte de ser el menor y mas temeroso de mis Yorkies) para manejar subidas de archivos a tu website. Con este widget se pretende crear una herramienta que te ayude a olvidarte de la complejidad de este asunto, sacando provecho de Yii Framework, jQuery, Ajax y UML/MVC

La implementación del widget en tu proyecto es muy simple, se hace en dos partes: Primero, Pones el widget en la vista o formulario en donde lo requieras y Segundo en algun controller pones un action fijo en cualquier controller, no solamente aquel del formulario (un action fijo es aquel que se coloca en el metodo de actions() del controller), este action tiene como proposito conectar el código javascript del widget con tu aplicación Yii.

Coco toma su funcionalidad de una librería PHP muy buena que consegui hace un año y que decidí implementar para Yii framework en forma de Widget. La licencia del autor de la libreria original es respetada y matiene sus creditos. Puedes hallarlo en el repositorio valums de github.


INSTALACION / INSTALL
---------------------

1. 	GIT Cloning

		cd /home/blabla/myapp/protected
		mkdir extensions
		cd extensions
		git clone git@bitbucket.org:christiansalazarh/coco.git

		[ES] Si no usas GIT simplemente copia el contenido de la extension directamente dentro de 'extensions'
		[EN] If you dont use GIT please copy the entire 'coco' folder into your extensions folder

2.	Setup 'config/main'

		'import'=>array(
			'application.models.*',
			'application.components.*',
			'application.extensions.coco.*',			// <------
		),

3.	[ES] Conecta el widget con tu aplicación web, usa cualquier action.
	[EN] Connect the widget wit your current application using a fixed Action in siteController (or a distinct controller if you prefer).

		[ES] edita
		[EN] must edit:

			myapp/protected/controllers/SiteController.php

		[ES] agrega un action fijo
		[EN] add a fixed action:

		IMPORTANT:
			Este action solo es requerido una vez para todo el proyecto !!
			This action is required only one time for all above project !!

			public function actions()
			{
				return array(
					'captcha'=>array(
						'class'=>'CCaptchaAction',
						'backColor'=>0xFFFFFF,
					),
					'page'=>array(
						'class'=>'CViewAction',
					),
					'coco'=>array(
						'class'=>'CocoAction',
					),
				);
			}


4.	[ES] Usa el widget en cualquier form.
	[EN] Use the widget in your form.

		<?php
			$this->widget('ext.coco.CocoWidget'
				,array(
					'id'=>'cocowidget1',

					'onCompleted'=>'function(id,filename,jsoninfo){  }',
					'onCancelled'=>'function(id,filename){ alert("cancelled "+filename); }',
					'onMessage'=>'function(m){ alert(m); }',

					'allowedExtensions'=>array('jpeg','jpg','gif','png'),
					'sizeLimit'=>2000000,
					'uploadDir' => 'assets/',
				)
			);
		?>


Extra Options
-------------

		'buttonText'=>'Find & Upload',
		'dropFilesText'=>'Drop Files Here !',
		'htmlOptions'=>array('style'=>'width: 300px; float: left; margin-right: 10px;'),
		'defaultControllerName'=>'site',
		'defaultActionName'=>'coco',

