### the form 
```html
<div id="contact_form">
  <form name="contact" action="">
    <fieldset>
      <div class="input-box">
        <label for="name" id="name_label">Name</label>
        <input type="text" name="name" id="name" minlength="3" placeholder="Monty" class="text-input" required />
      </div>

      <div class="input-box">
        <label for="email" id="email_label">Email</label>
        <input type="email" name="email" id="email" placeholder="example@tutsplus.com" class="text-input" />
      </div>

      <input type="submit" name="submit" class="button" id="submit_btn" value="Send" />
    </fieldset>
  </form>

</div>
```

### the js 
```js
<script>
  $(function () {
    $("form").validate();

    $("form").on("submit", function (e) {
      e.preventDefault();

      var dataString = $(this).serialize();
      // alert(dataString); return false;

      $.ajax({
        type: "POST",
        url: "bin/process.php",
        data: dataString,
        success: function () {
          $("#contact_form").html("<div id='message'> Success </div>");

        }
      });
    });
  });
</script>
```


## another way using post method

```html

<form action="/" id="searchForm">
  <input type="text" name="s" placeholder="Search...">
  <input type="submit" value="Search">
</form>
<!-- the result of the search will be rendered inside this div -->
<div id="result"></div>
```

### js

```js
<script>
// Attach a submit handler to the form
 $(function () {

    $( "#searchForm" ).submit(function( event ) {
    
      // Stop form from submitting normally
      event.preventDefault();
    
      // Get some values from elements on the page:
      var $form = $( this ),
        term = $form.find( "input[name='s']" ).val(),
        url = $form.attr( "action" );
    
      // Send the data using post
      var posting = $.post( url, { s: term } );
    
      // Put the results in a div
      posting.done(function( data ) {
        var content = $( data ).find( "#content" );
        $( "#result" ).empty().append( content );
      });
    });
 })
</script>
```

