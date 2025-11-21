<html lang="en">
    <head>
        <script type='text/javascript'>
        	function initEmbeddedMessaging() {
        		try {
        			embeddedservice_bootstrap.settings.language = 'en_US'; // For example, enter 'en' or 'en-US'

                    const customElement = document.querySelector('div#chat-container-region');
                    console.log("customElement:", customElement);
                    embeddedservice_bootstrap.settings.targetElement = customElement;
                    embeddedservice_bootstrap.settings.displayMode = 'inline';
        
        			embeddedservice_bootstrap.init(
        				'00DKj00000BqFBw',
        				'Messaging_for_In_App_and_Web',
        				'https://mduraipand-250112-382-demo.my.site.com/ESWMessagingforInAppa1736797486907',
        				{
        					scrt2URL: 'https://mduraipand-250112-382-demo.my.salesforce-scrt.com'
        				}
        			);
        		} catch (err) {
        			console.error('Error loading Embedded Messaging: ', err);
        		}
        	};
        </script>
        <script 
            type='text/javascript' 
            onload='initEmbeddedMessaging()'
            src='https://mduraipand-250112-382-demo.my.site.com/ESWMessagingforInAppa1736797486907/assets/js/bootstrap.min.js'>
        </script>
    </head>
    <body>
        <div id="chat-container-region" style="height: 700px; width: 500px">
        </div>
    </body>
</html>
