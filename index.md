<html>
<div id="chat-container" style="height: 800px; width: 1200px"></div>
<script type='text/javascript'>
	function initEmbeddedMessaging() {
		try {
			embeddedservice_bootstrap.settings.language = 'en_US'; // For example, enter 'en' or 'en-US'

			embeddedservice_bootstrap.settings.displayMode = 'inline';
			embeddedservice_bootstrap.settings.headerEnabled = false; // Optional
			const targetChatElement = document.querySelector('div#chat-container');
			console.log('targetChatElement', targetChatElement);
			embeddedservice_bootstrap.settings.targetElement = targetChatElement;

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
<script type='text/javascript' src='https://mduraipand-250112-382-demo.my.site.com/ESWMessagingforInAppa1736797486907/assets/js/bootstrap.min.js' onload='initEmbeddedMessaging()'></script>
</html>
