

# Form HTML


```php
<form action="" method="POST">
// Field

// Security check
<?php wp_nonce_field('dev-survey'); ?>
<input class="survey-submit btn btn-primary" type="submit" name="submit" value="Submit">
</form>
```

# Handle form submission at init action

```php
public function dev_survey_submit_form() {
        if ( ! empty( $_POST['submit'] ) && ! empty( $_POST['_wpnonce'] ) && wp_verify_nonce( $_POST['_wpnonce'], 'dev-survey' ) ) {
            
        }        
    }
add_action('init', 'dev_survey_submit_form' );
```
