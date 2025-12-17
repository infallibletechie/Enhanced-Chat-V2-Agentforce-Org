<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1, minimum-scale=1">
  <title>Inline Chat</title>
  <style>
    * { margin: 0; padding: 0; box-sizing: border-box; }
    body {
      min-height: 100vh;
      display: flex;
      align-items: center;
      justify-content: center;
      background: #f0f0f0;
      font-family: sans-serif;
    }
    #chat-container {
      width: 400px;
      height: 600px;
      border: 2px solid #ccc;
      background: #fff;
      position: relative;
    }
  </style>
</head>
<body>
  <div id="chat-container"></div>

  <script type='text/javascript'>

    window.addEventListener("beforeunload", () => {
        if(embeddedservice_bootstrap.utilAPI) {
            embeddedservice_bootstrap.utilAPI.removeAllComponents()
        }
    });
    function initEmbeddedMessaging() {
      try {
        embeddedservice_bootstrap.settings.language = 'en_US';
        embeddedservice_bootstrap.settings.displayMode = 'inline';
        embeddedservice_bootstrap.settings.targetElement = document.getElementById('chat-container');

        embeddedservice_bootstrap.init(
          '00DKj00000BqFBw',
          'Messaging_for_In_App_and_Web',
          'https://mduraipand-250112-382-demo.my.site.com/ESWMessagingforInAppa1736797486907',
          {
            scrt2URL: 'https://mduraipand-250112-382-demo.my.salesforce-scrt.com'
          }
        );
      } catch (err) {
        console.error('Error loading Embedded Messaging:', err);
      }
    }
  </script>
  <script type='text/javascript' src='https://mduraipand-250112-382-demo.my.site.com/ESWMessagingforInAppa1736797486907/assets/js/bootstrap.min.js' onload='initEmbeddedMessaging()'></script>
</body>
</html>
