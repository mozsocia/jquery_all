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
