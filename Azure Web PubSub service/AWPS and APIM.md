# Expand your application with real-time messaging API capability with Web PubSub and API Management 

Businesses everywhere are looking to extend their operations as a digital platform, creating new channels, finding new customers and driving deeper engagement with existing ones. Now, with the [API Management (APIM)](https://azure.microsoft.com/services/api-management) and [Web PubSub service (AWPS)](https://azure.microsoft.com/en-us/services/web-pubsub/#overview), you are available to expand real-time messaging capability of your application with a consistent and modern API gateways. 
* Build apps faster and deliver immediate value to your customers through API-first approaches. 
* Transform your legacy services into modern REST-based APIs or WebScoket APIs.
* Consistent experience to manage APIs (REST and WebSocket) across clouds and on-premises.


## Setup Azure Web PubSub service 
1. Create resource of Web PubSub service ***AWPS1***.
2. Go to the  ***AWPS1*** in the portal. 
3. Go to the *Keys* blade.
    * Get the *Host name*
    * Get the *Client access URL* of ***APIMHub*** for internal quick testing.

:::image type="content" source="resources/AWPS-Keys.png" alt-text="Screenshot of getting Azure Web PubSub service keys.":::

## Setup Azure API Management 
1. Create resource of API Management ***apim-demo01***.
2. Go to the ***apim-demo01*** in the portal. 
3. Go to the *API* blade and create a WebSocket API
    * Create WebSocket API 
        * Name: ***awpsapi***
        * WebSocket URL：wss://\<*AWPS-host-name*\>/client/hubs/\<*hub-name*\>
        * API URL suffix: client/hubs/\<*hub-name*\> 
    
    :::image type="content" source="resources/APIM-WebSocketAPI-Create.png" alt-text="Screenshot of creating WebSocket API in APIM.":::

    :::image type="content" source="resources/APIM-WebSocketAPI-Create-Parameters.png" alt-text="Screenshot of parameters for WebSocket API.":::

4. Quick validation of the ***awpsapi***
    * Switch to the *Test* tab. 
    * Add a new paremeter
        * NAME: access_token
        * VALUE: Get the access token value from the *Client access URL* of AWPS resource
    * Click *Connect* button and it should connect successfully. 

    :::image type="content" source="resources/APIM-WebSocketAPI-Validate.png" alt-text="Screenshot of parameters for WebSocket API.":::

## Use the Web PubSub Client demo with APIM

Now, the Web PubSub is exposed as APIM WebSocket API and we could use this API directly with the [Web PubSub Client demo](https://azure.github.io/azure-webpubsub/demos/clientpubsub). 

1. Go to the *Overview* blade of ***awpsapi*** in the portal, and get the *Gateway URL*.
2. Get the host name of APIM from the *Gateway URL*.
3. Replace the host name of Web PubSub with the host name of APIM in *Client access URL*. 
4. Use the new *Client access URL* with the demo. 