<html lang="en">
    <style>
        .chat-container-design {
            width: 500px;
            height: 700px;
            display: flex;
            background: #fff;
            border-radius: 10px;
            border: 1px solid #ddd;
            flex-direction: column;
            box-shadow: 0 2px 8px rgba(0, 0, 0, 0.1);
        }
    </style>
    <body>
        <div id="chat-container-region" class="chat-container-design">
        </div>
        <script type='text/javascript'>
        	function initEmbeddedMessaging() {
        		try {
        			embeddedservice_bootstrap.settings.language = 'en_US'; // For example, enter 'en' or 'en-US'

                    const customElement = document.querySelector('#chat-container-region');
                    console.log("customElement:", customElement);
                    //embeddedservice_bootstrap.settings.targetElement = customElement;
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
    </body>
</html>
