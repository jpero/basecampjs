# basecampjs

This is a JavaScript wrapper for the Basecamp API. It covers everything in the API except file attachments for comments and messages. For the API to work it has to be used in an environment like AIR or browser extensions where cross-domain XMLHttpRequest calls are allowed.

Here is an example of getting back an Array of projects from Basecamp.

    var basecamp = new Basecamp("your.basecamp.url", "api_token");
    basecamp.projects({
      success: function( projects_xml ) {
        var projects = Basecamp.Project.from_xml( projects_xml );
        alert( projects.length );
      }
    });

Here is an example of how to create a new message assuming you've already used the API to retrieve the desired project_id, message_category_id and person_id.

    var message = new Basecamp.Message({
      title: "Testing from API",
      body: "This is a test from the JavaScript API wrapper.",
      category_id: message_category_id
    });
    basecamp.post_message( project_id, message, [person_id], {
      success: function( message_xml ) {
        var message = Basecamp.Message.from_xml( message_xml )[0];
        alert( message.id );
      }
    });


## Documentation

First place to look is the actual [Basecamp API documentation](http://developer.37signals.com/basecamp/). Currently this API follows their [Ruby wrapper](http://developer.37signals.com/basecamp/basecamp.rb) very closely. Other than that ... its all code for now. :)


## License

Licensed under the [MIT](http://www.opensource.org/licenses/mit-license.php) license.

Copyright (c) 2008 [Brandon Aaron](http://brandonaaron.net)