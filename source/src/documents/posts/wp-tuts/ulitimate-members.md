

# add custom tab to account page

```
/***
*** @add custom tab to account page
***/
add_filter('um_account_page_default_tabs_hook', 'my_custom_tab_in_um', 100 );
function my_custom_tab_in_um( $tabs ) {
    $tabs[800]['extrainfo']['icon'] = 'um-faicon-pencil';
    $tabs[800]['extrainfo']['title'] = 'Extra info';
    $tabs[800]['extrainfo']['custom'] = true;
    return $tabs;
}
    
/***
*** @make our new tab hookable
***/
add_action('um_account_tab__extrainfo', 'um_account_tab__extrainfo');
function um_account_tab__extrainfo( $info ) {
    global $ultimatemember;
    extract( $info );

    $output = $ultimatemember->account->get_tab_output('extrainfo');
    if ( $output ) { echo $output; }
}

/***
*** @render content in the tab
***/ 
add_filter('um_account_content_hook_extrainfo', 'um_account_content_hook_extrainfo');
function um_account_content_hook_extrainfo( $output ){
    ob_start();
    $user_id = get_current_user_id();
    ?>
    <div class="um-account-heading uimob340-hide uimob500-hide"><i class="um-faicon-user"></i>Extra Info</div>  

    <div class="um-field">      
        <div data-key="emergancy_profile" class="um-field um-field-emergancy_profile um-field-text">
            <div class="um-field-label">
                <label for="emergancy_profile">Emergancy call</label>
                <div class="um-clear"></div>
            </div>
            <div class="um-field-area">
                <input type="text" data-key="emergancy_profile" data-validate="" placeholder="" value="<?php echo get_user_meta( $user_id, 'emergancy_profile', true ); ?>" id="emergancy_profile" name="emergancy_profile" class="um-form-field valid ">                               
            </div>
        </div>      
    </div>  

    <div class="um-field">      
        <div data-key="description" class="um-field um-field-description um-field-text">
            <div class="um-field-label">
                <label for="description">Bio</label>
                <div class="um-clear"></div>
            </div>
            <div class="um-field-area">
                <textarea name="description" id="description" rows="10"><?php echo get_user_meta( $user_id, 'description', true ); ?></textarea>                            
            </div>
        </div>      
    </div>
    <div class="um-col-alt um-col-alt-b">
        <input type="hidden" name="user_id" value="<?php echo $user_id; ?>" >
        <div class="um-left"><input type="submit" name="um_account_submit" id="um_account_submit" value="<?php _e('Update Account','ultimatemember'); ?>" class="um-button" /></div>
        <div class="um-clear"></div>
    </div>
    <?php
        
    $output .= ob_get_contents();
    ob_end_clean();
    return $output;
}

/***
*** @listen to account update
***/ 
add_action('um_submit_account_details', 'check_for_other_fields');
function check_for_other_fields() {
    global $ultimatemember;
    $user_id = $_POST['user_id'];

    
    if ( $_POST['description'] ) {  
        update_user_meta( $user_id,'description',  $_POST['description'] );  
    }
    if ( $_POST['emergancy_profile'] ) {
        
        update_user_meta( $user_id,'emergancy_profile', sanitize_text_field( $_POST['emergancy_profile'] ) );  
    }

    $tab = ( get_query_var('um_tab') ) ? get_query_var('um_tab') : 'general';

    $url = $ultimatemember->account->tab_link( $tab );
        
    $url = add_query_arg( 'updated', 'account', $url );

    exit( wp_redirect( $url ) );
}
```

# Get core page

```
$core_pages = get_option('um_core_pages'); 
$login = $core_pages['login'];
```