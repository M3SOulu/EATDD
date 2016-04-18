---
layout: page
title: Contact
permalink: /contact/
---

<div class="contact">
  <h2 class="page-header">Get in touch</h2>
  <div class="row">
    <div class="col-md-6">
      <form id="contact_form">
        <div class="form-group">
          <label for="id_name" class="control-label">Name</label>
          <input type="text" class="form-control" id="id_name" name="name">
        </div>
        <div class="form-group">
          <label for="id_email" class="control-label">Email</label>
          <input type="email" class="form-control" id="id_email" name="email">
        </div>
        <div class="form-group">
          <label for="id_subject" class="control-label">Subject</label>
          <input type="text" class="form-control" name="subject" id="id_subject">
        </div>
        <div class="form-group">
          <label for="id_message" class="control-label">Message</label>
          <textarea class="form-control" name="message" id="id_message" rows="7"></textarea>
        </div>
        <div class="form-group">
          <button type="button" class="btn btn-primary" id="id_send">
            <span class="glyphicon glyphicon-send" style="margin-right: 3px"></span> <span class="text">Send</span>
          </button>
        </div>
      </form>
    </div>
  </div>
</div>

<script>
  $(function () {
    $("#id_send").click(function () {
      var from_email = $("#id_email").val();
      var from_name = $("#id_name").val().length > 0 ? $("#id_name").val() : $("#id_email").val();
      var subject = '[VALUE Project Contact] ' + $("#id_subject").val();
      var message = $("#id_message").val();

      var errors = '';
      if (from_email === '') {
        $("#id_email").closest(".form-group").addClass("has-error");
        errors += 'Email is a required field. '
      }
      else {
        $("#id_email").closest(".form-group").removeClass("has-error");
      }

      if (message === '') {
        $("#id_message").closest(".form-group").addClass("has-error");
        errors += 'Message is a required field.'
      }
      else {
        $("#id_message").closest(".form-group").removeClass("has-error");
      }

      if (errors.length > 0) {
        alert(errors);
      }
      else {
        $.ajax({
          type: "POST",
          url: "https://mandrillapp.com/api/1.0/messages/send.json",
          data: {
            'key': '-bPYycDPFKkZ6AGg-MJOvQ',
            'message': {
              'from_name': from_name,
              'from_email': from_email,
              'to': [
                  {
                    'email': 'burak.turhan@oulu.fi',
                    'name': 'Burak Turhan',
                    'type': 'to'
                  }
                ],
              'headers': {
                  'Reply-To': from_email
              },
              'autotext': 'true',
              'subject': subject,
              'html': message
            }
          },
          beforeSend: function () {
            $("#id_send").prop("disabled", true);
            $("#id_send span.text").text("Sending…");
          },
          success: function (data) {
            alert("Thanks for your message! We will get back to you soon!");
            $("#contact_form input, #contact_form textarea").val("");
          },
          error: function () {
            alert("An error ocurred while trying to send your message. Please try again later.")
          },
          complete: function () {
            $("#id_send").prop("disabled", false);
            $("#id_send span.text").text("Send");
          }
         });
      }

    });
  });
</script>
