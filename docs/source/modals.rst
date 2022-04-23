HTML Example::
  <div class="dialog-container" id="my-dialog" aria-hidden="true" aria-labelledby="my-dialog-title"
      aria-describedby="my-dialog-description">
      <div class="dialog-overlay" data-a11y-dialog-hide></div>
      <div class="dialog-content" role="document">
          <button data-a11y-dialog-hide class="dialog-close" aria-label="Close this dialog window">
              &times;
          </button>

          <h1 id="my-dialog-title"></h1>

          <p id="my-dialog-description">
              Build with Python Flask
          </p>

          <form>
              <label for="email">Email (required)</label>
              <input type="email" name="EMAIL" id="email" placeholder="john.doe@gmail.com" required />
              <button type="submit" name="button">Sign up</button>
          </form>
      </div>
  </div>
.. code-block:: rst
