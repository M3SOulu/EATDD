---
layout: page
title: Contact
permalink: /contact/
---

<div class="contact">
  <h2 class="page-header">Get in touch</h2>
  <div class="row">
    <div class="col-md-6">
      <form action="https://formspree.io/burak.turhan@oulu.fi" method="POST">
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
          <button type="submit" class="btn btn-primary" id="id_send">
            <span class="glyphicon glyphicon-send" style="margin-right: 3px"></span> <span class="text">Send</span>
          </button>
        </div>
      </form>
    </div>
  </div>
</div>

