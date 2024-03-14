<html>
<script type='text/javascript'>
	function initEmbeddedMessaging() {
		try {
			embeddedservice_bootstrap.settings.language = 'en_US'; // For example, enter 'en' or 'en-US'

			embeddedservice_bootstrap.init(
				'00DHo000002fRR9',
				'MIAW_BOT',
				'https://infallibletechie2-dev-ed.develop.my.site.com/ESWMIAWBOT1710450128999',
				{
					scrt2URL: 'https://infallibletechie2-dev-ed.develop.my.salesforce-scrt.com'
				}
			);
		} catch (err) {
			console.error('Error loading Embedded Messaging: ', err);
		}
	};
</script>
<script type='text/javascript' src='https://infallibletechie2-dev-ed.develop.my.site.com/ESWMIAWBOT1710450128999/assets/js/bootstrap.min.js'></script>

    <button id="launchChatButton" onclick="launchChat()">
        Log your Issue
    </button>

    <script>
        window.onload=function() {      
        
            console.log( 'Inside onload' );
            let startMessaging = sessionStorage.getItem(
                'messagingStartCheck'
            );

            if ( 
                startMessaging &&
                startMessaging === 'YES'
            ) {

                console.log( 'Messaging was in progress' );
                initEmbeddedMessaging();

  		if ( embeddedservice_bootstrap.utilAPI ) {
                
			embeddedservice_bootstrap.utilAPI.launchChat();

  		}
                
            }
            
        };
        function launchChat() {
        
            sessionStorage.setItem(
                'messagingStartCheck',
                'YES'
            );
            initEmbeddedMessaging();
            console.log("Loading Messaging now");
            setTimeout(() => {
                embeddedservice_bootstrap.utilAPI
                    .launchChat()
                    .then(() => {
                        console.log("Inside Launch Chat");
                    })
                    .catch(() => {
                        console.log("Inside Launch Chat catch Block");
                    })
                    .finally(() => {
                        console.log("Inside Launch Chat finally Block");
                    });
            }, 2000);
            
        }
    </script>
</html>
