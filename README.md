Learning JavaScript Design Patterns
=============

> Learning JavaScript Design Patterns is released under a Creative Commons Attribution-Noncommercial-No Derivative Works 3.0 unported license. It is available for purchase via O'Reilly Media but will remain available for both free online and as a physical (or eBook) purchase for readers wishing to support the project.

# Preface

Design patterns are reusable solutions to commonly occurring problems in software design. They are both exciting and a fascinating topic to explore in any programming language.

One reason for this is that they help us build upon the combined experience of many developers that came before us and ensure we structure our code in an optimized way, meeting the needs of problems we're attempting to solve.

Design patterns also provide us a common vocabulary to describe solutions. This can be significantly simpler than describing syntax and semantics when we're attempting to convey a way of structuring a solution in code form to others.

In this book we will explore applying both classical and modern design patterns to the JavaScript programming language.

## Target Audience

This book is targeted at professional developers wishing to improve their knowledge of design patterns and how they can be applied to the JavaScript programming language.

Some of the concepts covered (closures, prototypal inheritance) will assume a level of basic prior knowledge and understanding. If you find yourself needing to read further about these topics, a list of suggested titles is provided for convenience.

If you would like to learn how to write beautiful, structured and organized code, I believe this is the book for you.

```javascript
$( "#chatForm" ).on( "submit", function(e) {
    e.preventDefault();

    // Collect the details of the chat from our UI
    var text = $( "#chatBox" ).val(),
        from = $( "#fromBox" ).val(),
        to = $( "#toBox" ).val();

    // Publish data from the chat to the newMessage topic
    mediator.publish( "newMessage" , { message: text, from: from, to: to } );
});

// Append new messages as they come through
function displayChat( data ) {
    var date = new Date(),
        msg = data.from + " said \"" + data.message + "\" to " + data.to;

    $( "#chatResult" )
        .prepend("<p>" + msg + " (" + date.toLocaleTimeString() + ")</p>");
}

// Log messages
function logChat( data ) {
    if ( window.console ) {
        console.log( data );
    }
}



// Subscribe to new chat messages being submitted
// via the mediator
mediator.subscribe( "newMessage", displayChat );
mediator.subscribe( "newMessage", logChat );


// The following will however only work with the more advanced implementation:

function amITalkingToMyself( data ) {
    return data.from === data.to;
}

function iAmClearlyCrazy( data ) {
    $( "#chatResult" ).prepend("<p>" + data.from + " is talking to himself.</p>");
}

mediator.Subscribe( amITalkingToMyself, iAmClearlyCrazy );