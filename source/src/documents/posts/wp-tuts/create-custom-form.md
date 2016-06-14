

Form

```php
<form action="" method="POST">
// Field

// Security check
<?php wp_nonce_field('dev-survey'); ?>
<input class="survey-submit btn btn-primary" type="submit" name="submit" value="Submit">
<input type="hidden" name="survey-submission" value="1" />
</form>
```

Handle form submission at init action

```php
public function dev_survey_submit_form() {
        
        if ( isset( $_POST['survey-submission'] ) && '1' == $_POST['survey-submission'] ) {
            $nonce = $_REQUEST['_wpnonce'];
            

            if ( ! wp_verify_nonce( $nonce, 'dev-survey' )  ) {
                
                die( 'Security check' ); 

            } else {
                var_dump($_POST);               
                die();
            }
        } // check survey-submission
    }
add_action('init', 'dev_survey_submit_form' );
```
