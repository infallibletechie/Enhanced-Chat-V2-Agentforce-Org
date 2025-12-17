<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1, minimum-scale=1">
  <title>Responsive Inline Chat</title>
  <style>
    :root {
      --chat-border: #d8dde6;
      --chat-bg: #f4f6f9;
    }

    * { margin: 0; padding: 0; box-sizing: border-box; }

    body {
      min-height: 100vh;
      display: flex;
      align-items: center;
      justify-content: center;
      background: #f0f2f5;
      font-family: -apple-system, BlinkMacSystemFont, "Segoe UI", Roboto, Helvetica, Arial, sans-serif;
    }

    /* Responsive Container */
    #chat-wrapper {
      width: 100%;
      max-width: 450px; /* Desktop width */
      height: 700px;
      max-height: 90vh; /* Prevents overflow on short screens */
      margin: 10px;
      background: #fff;
      border-radius: 12px;
      box-shadow: 0 8px 24px rgba(0,0,0,0.1);
      overflow: hidden;
      border: 1px solid var(--chat-border);
      position: relative;
      display: flex;
      flex-direction: column;
    }

    #chat-container {
      flex: 1;
      width: 100%;
      height: 100%;
    }

    /* Loading State Styles */
    .chat-loading-overlay {
      position: absolute;
      top: 0; left: 0; right: 0; bottom: 0;
      display: flex;
      flex-direction: column;
      align-items: center;
      justify-content: center;
      background: #ffffff;
      z-index: 10;
      transition: opacity 0.3s ease;
    }

    .spinner {
      width: 40px;
      height: 40px;
      border: 4px solid #f3f3f3;
      border-top: 4px solid #0070d2; /* Salesforce Blue */
      border-radius: 50%;
      animation: spin 1s linear infinite;
      margin-bottom: 15px;
    }

    @keyframes spin {
      0% { transform: rotate(0deg); }
      100% { transform: rotate(360deg); }
    }

    /* Mobile adjustments */
    @media (max-width: 480px) {
      #chat-wrapper {
        margin: 0;
        height: 100vh;
        max-height: 100vh;
        border-radius: 0;
        max-width: 100%;
      }
    }
  </style>
</head>
<body>

  <div id="chat-wrapper" aria-live="polite">
    <div id="loading-state" class="chat-loading-overlay">
      <div class="spinner"></div>
      <p style="color: #706e6b; font-size: 14px;">Connecting to Support...</p>
    </div>
    
    <div id="chat-container"></div>
  </div>

  <script type='text/javascript'>
    function initEmbeddedMessaging() {
      try {
        embeddedservice_bootstrap.settings.language = 'en_US';
        embeddedservice_bootstrap.settings.displayMode = 'inline';
        embeddedservice_bootstrap.settings.targetElement = document.getElementById('chat-container');

        // Event listener to hide loading state when chat is ready
        window.addEventListener("onEmbeddedMessagingReady", () => {
          const loader = document.getElementById('loading-state');
          if (loader) loader.style.opacity = '0';
          setTimeout(() => loader?.remove(), 300); // Clean up DOM
          console.log("MIAW Initialized Successfully");
        });

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
        showErrorState();
      }
    }

    function showErrorState() {
      const loader = document.getElementById('loading-state');
      if (loader) {
        loader.innerHTML = '<p style="padding: 20px; text-align: center;">Chat is currently unavailable. Please refresh or try again later.</p>';
      }
    }
  </script>

  <script 
    type='text/javascript' 
    src='https://mduraipand-250112-382-demo.my.site.com/ESWMessagingforInAppa1736797486907/assets/js/bootstrap.min.js' 
    onload='initEmbeddedMessaging()'
    onerror='showErrorState()'>
  </script>

</body>
</html>
