Modals
======

Modal dialogs use `a11y-dialog`_. 

Example HTML, you'd create one of these blocks for every modal.

.. code-block:: html

  <div class="dialog-container" id="my-dialog" aria-hidden="true">
      <div class="dialog-overlay" data-a11y-dialog-hide></div>
      <div class="dialog-content" role="document">
          <button data-a11y-dialog-hide class="dialog-close" aria-label="Close this dialog window">
              &times;
          </button>
          <p>Here is the content!</p>
      </div>
  </div>

.. _a11y-dialog: https://github.com/KittyGiraudel/a11y-dialog

Call it using JavaScript:

.. code-block:: javascript

  var dialogEl = document.getElementById('my-dialog')
  var dialog = new A11yDialog(dialogEl)

  dialog.on('show', function (dialogEl, triggerEl) {
    console.log(dialogEl)
    console.log(triggerEl)
  })
