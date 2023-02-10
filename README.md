# Ticketing Integration Accelerator for Cumulocity IoT

This accelerator allows to integrate Cumulocity IoT with Ticketing Platforms like webMethods AgileApps, Zendesk, etc.

## Features
* Create tickets for device alarms in Ticketing Platform.
* View tickets (including comments) related to devices in Cumulocity IoT.

## Installation
1. Install Ticketing Integration microservice on your Cumulocity IoT tenant. Refer to https://github.com/SoftwareAG/c8y-ticketing-integration-microservice.
2. Install UI widgets on your Cumulocity IoT tenant. It comprises three widgets, Setup widget, Viewer widget and Alarms widget.
    * For Cumulocity IoT version >= 10.16 and Application Builder version >= 2.0.0, refer to https://github.com/SoftwareAG/c8y-ticketing-integration-plugin.
    * For older Cumulocity IoT versions, refer to
        * https://github.com/SoftwareAG/c8y-ticketing-integration-setup-widget for Setup widget.
        * https://github.com/SoftwareAG/c8y-ticketing-integration-viewer-widget for Viewer widget.
        * https://github.com/SoftwareAG/c8y-ticketing-integration-alarms-widget for Alarms widget.
3. Integrate with webMethods AgileApps directly using Setup widget. For any other ticketing platform, first create an API and integration using an integration platform like webMethods.io. Refer to Zendesk example below.

## Examples

### Create API and Integration with Zendesk using webMethods.io
1. Download ZendeskCumulocityIoTIntegration.zip from the Releases section.
2. Unzip the ZendeskCumulocityIoTIntegration.zip.
3. Create a Project in webMethods.io.
4. Import following three FlowServices to your project.
    1. getTickets using getTickets.zip
    2. createTicket using createTicket.zip
    3. getTicketComments using getTicketComments.zip
5. Add "New Account" for "Zendesk_Custom" REST Connector. Following information is required
    1. Zendesk tenant base url.
    2. OAuth consumer id, consumer secret and access token.
    3. Set Hostname Verifier to org.apache.http.conn.ssl.NoopHostnameVerifier.
    4. Set Refresh access token to false.
    5. Set Session management to none.
6. Create a new API from scratch with following resources
    1. GET /tickets and map it to getTickets FlowService.
    2. POST /tickets and map it to createTicket FlowService.
    3. GET /tickets/{id}/comments and map it to getTicketComments FlowService.
7. Find API endpoint in Basic information section of API Detail page.

______________________
These tools are provided as-is and without warranty or support. They do not constitute part of the Software AG product suite. Users are free to use, fork and modify them, subject to the license agreement. While Software AG welcomes contributions, we cannot guarantee to include every contribution in the master project.	
