# Sending form data
what happens when a user submits a form — where does the data go, and how do we handle it when it gets there? 

### Client/server architecture
a client (usually a web browser) sends a request to a server , using the HTTP protocol. The server answers the request using the same protocol.

On the client side: defining how to send the data
The <form> element defines how the data will be sent 
The action attribute
The action attribute defines where the data gets sent

        <form action="https://example.com">
When specified with no attributes, as below, the <form> data is sent to the same page that the form is present on
### The method attribute
The method attribute defines how data is sent
 let's step back and examine how HTTP works. Each time you want to reach a resource on the Web, the browser sends a request to a URL. An HTTP request consists of two parts: a header that contains a set of global metadata about the browser's capabilities, and a body that can contain information necessary for the server to process the specific request. 
1. The GET method
ask the server to send back a given resource: Ithis case, the browser sends an empty body. Because the body is empty, if a form is sent using this method the data sent to the server is appended to the URL.

The data is appended to the URL as a series of name/value pairs. After the URL web address has ended, we include a question mark (?) followed by the name/value pairs, each one separated by an ampersand (&). 

2. The POST method
a response data provided in the body of the HTTP request
data included in the request body instead:

### Viewing HTTP requests
to show the request 
Open the developer tools.
Select "Network"
Select "All"
Select "foo.com" in the "Name" tab
Select "Headers"

#####  The only thing displayed to the user is the URL called. As we mentioned above, with a GET request the user will see the data in their URL bar, but with a POST request they won't. This can be very important for two reasons:

1. If you need to send a password (or any other sensitive piece of data), never use the GET method or you risk displaying it in the URL bar, which would be very insecure.
2. If you need to send a large amount of data, the POST method is preferred because some browsers limit the sizes of URLs. In addition, many servers limit the length of URLs they accept.

### Security issues
The problems never come from the HTML forms themselves — they come from how the server handles data.

### Be paranoid: Never trust your users
1. Escape potentially dangerous characters.
2. Limit the incoming amount of data to allow only what's necessary.
3. Sandbox uploaded files.

You should avoid many/most problems if you follow these three rules, but it's always a good idea to get a security review performed by a competent third party. Don't assume that you've seen all the possible problems.


Refernces:
1. [Sending Form Data](https://developer.mozilla.org/en-US/docs/Learn/Forms/Sending_and_retrieving_form_data)
2. [HTML5 Forms Reference](https://htmlreference.io/forms/)
3. [Video Series on Styling HTML5 Forms](https://www.youtube.com/playlist?list=PL4cUxeGkcC9g5_p_BVUGWykHfqx6bb7qK) 
