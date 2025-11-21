<html lang="en">
    <head>
        <title>Chat</title>
        <style>
            body {
                font-family: Arial, sans-serif;
                background-color: #f7f8fa;
                display: flex;
                justify-content: center;
                align-items: center;
                height: 100vh;
                margin: 0;
            }
            .chat-container {
                background: #fff;
                border: 1px solid #ddd;
                border-radius: 10px;
                width: 400px;
                padding: 16px;
                box-shadow: 0 2px 8px rgba(0, 0, 0, 0.1);
                display: flex;
                flex-direction: column;
            }
            .chat-input-area {
                display: flex;
                border: 1px solid #ccc;
                border-radius: 20px;
                padding: 8px 12px;
                background: #f1f1f1;
            }
            .chat-input {
                flex: 1;
                border: none;
                background: transparent;
                outline: none;
                font-size: 16px;
                padding: 6px;
            }
            .send-button {
                background-color: #0078ff;
                border: none;
                color: white;
                border-radius: 50%;
                width: 36px;
                height: 36px;
                cursor: pointer;
                font-size: 16px;
                display: flex;
                align-items: center;
                justify-content: center;
                transition: background 0.2s;
            }
            .send-button:hover {
                background-color: #005fd1;
            }
            /* --- CSS for Styling the Button --- */
            .send-message-button {
                background-color: #00008b;
                color: white;
                padding: 15px 30px;
                font-size: 18px;
                font-weight: bold;
                cursor: pointer;
                border: none;
                display: inline-block;
                text-align: center;
                border-radius: 5px;
                box-shadow: 0 0 0 2px white;
                outline: 2px solid #00008b;
            }
            .send-message-button:hover {
                background-color: #0000a0;
            }
        </style>

        <script type = "text/javascript">
            function initEmbeddedMessaging() {
                try {
                    embeddedservice_bootstrap.settings.language = 'en_US'; // For example, enter 'en' or 'en-US'
                    const myElement = document.querySelector('.chatContainer');
                    embeddedservice_bootstrap.settings.targetElement = myElement;
                    embeddedservice_bootstrap.settings.displayMode = 'inline';
                    
                    // Hiding Chat Button on page load
                    embeddedservice_bootstrap.settings.hideChatButtonOnLoad = true;
                    
                    /* START:: Conversation Opened Listener */
                    window.addEventListener("onEmbeddedMessagingConversationOpened", (event) => {
                        hideChatContainer();
                    });
                    /* END:: Conversation Opened Listener */
        
                    /* START:: Conversation Closed Listener */
                    window.addEventListener("onEmbeddedMessagingWindowClosed", (event) => {
                        showChatContainer();
                    });
                    /* END:: Conversation Closed Listener */
        
                    /* START:: Button Created Listener */
                    window.addEventListener("onEmbeddedMessagingButtonCreated", (event) => {
                        showChatContainer();
                    });
                    /* END:: Button Created Listener */
        
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
            } 
        </script>
        <script 
            type='text/javascript' 
            onload='initEmbeddedMessaging()'
            src='https://mduraipand-250112-382-demo.my.site.com/ESWMessagingforInAppa1736797486907/assets/js/bootstrap.min.js' >
        </script>
    </head>
    
    <body>
        <div>
            Welcome to our Chat Service!
            <br/><br/>
        </div>
        <div class="chatContainer">
        </div>
        <div class="chat-container">
            <div>
                Please select the menu or enter the message to get started.
                <br/>
            </div>
            <div>
                <br/><br/>
                <button class="send-message-button" id="orderButton">
                    Need help with my Order
                </button>
                <br/><br/>
                <button class="send-message-button" id="caseButton">
                    Need help with my Case
                </button>
                <br/><br/>
            </div>
            <div class="chat-input-area">
                <input type="text" id="chatInput" class="chat-input" placeholder="Type a message..." />
                <button class="send-button" id="sendBtn">➤</button>
            </div>
        </div>

        <script>
            function showChatContainer() {
                const chatContainer = document.querySelector('.chat-container');
                chatContainer.style.display = 'block';
            }

            function hideChatContainer() {
                const chatContainer = document.querySelector('.chat-container');
                chatContainer.style.display = 'none';
            }
            
            function launchChat(message) {
                embeddedservice_bootstrap.utilAPI.launchChat()
                    .then(() => {
                        console.log('Successfully launched Messaging');
                        sendMessageToChat(message);
                    })
                    .catch(() => {
                        console.log('Some error occurred when launching Messaging');
                    })
                    .finally(() => {
                        console.log('Successfully launched Messaging - Finally');
                    });
            }
            
            function sendMessageToChat(message) {
                setTimeout(() => {
                    embeddedservice_bootstrap.utilAPI.sendTextMessage(message)
                        .then(() => {
                            console.log("Message sent");
                        })
                        .catch(() => {
                            console.log("Message not sent");
                        })
                        .finally(() => {
                            console.log("Message sent - finally");
                        });
                }, 12000);
            }
            
            const sendBtn = document.getElementById('sendBtn');
            const chatInput = document.getElementById('chatInput');
            sendBtn.addEventListener('click', () => {
                const message = chatInput.value.trim();
                if (message) {
                    console.log(message);
                    chatInput.value = '';
                    hideChatContainer();
                    launchChat(message);
                } else {
                    alert("Please enter a message first!");
                }
            });
            // Allow pressing Enter to send the message
            chatInput.addEventListener('keypress', (e) => {
                if (e.key === 'Enter') {
                    sendBtn.click();
                }
            });
            
            // Get the button element using its ID
            const orderButton = document.getElementById('orderButton');
            // Add an event listener that runs a function when the button is clicked
            orderButton.addEventListener('click', function() {
                // Get the text content of the button
                const orderButtonText = orderButton.textContent.trim();
                // Display the text in the browser's console
                console.log(orderButtonText);
                launchChat(orderButtonText);
            });
            
            // Get the button element using its ID
            const caseButton = document.getElementById('caseButton');
            // Add an event listener that runs a function when the button is clicked
            caseButton.addEventListener('click', function() {
                // Get the text content of the button
                const caseButtonText = caseButton.textContent.trim();
                // Display the text in the browser's console
                console.log(caseButtonText);
                launchChat(caseButtonText);
            }); 
        </script>
    </body>
</html>
