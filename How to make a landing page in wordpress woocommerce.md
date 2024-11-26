# 1. Add the checkout form to the product page

## Create a child theme for your theme

### 1. Prepare for Child Theme Creation

Before starting, identify the name of the parent theme you want to customize. You’ll need this for the child theme setup.

- **Parent Theme Name**: You can find it in the WordPress dashboard under **Appearance > Themes**.
- **Location**: Parent themes are located in the `wp-content/themes/` directory.

---

### 2. Create the Child Theme Folder

1. **Access Your WordPress Files**:
    
    - Use an FTP client (like FileZilla) or the file manager in your hosting control panel to access the `wp-content/themes/` directory.
2. **Create a New Folder**:
    
    - Inside the `themes` directory, create a new folder. Name it something logical, like `parent-theme-child`. Replace `parent-theme` with your actual parent theme’s folder name.
    
    Example: If your parent theme is named `twentytwentyone`, name the folder `twentytwentyone-child`.
    

---

### 3. Add the `style.css` File

1. **Create the `style.css` File**:

    - Inside the child theme folder, create a new file named `style.css`.
2. **Add the Required Header**:

```
/*
Theme Name: Parent Theme Child
Theme URI: https://example.com
Description: A child theme of Parent Theme.
Author: Your Name
Author URI: https://yourwebsite.com
Template: parent-theme-folder-name
Version: 1.0.0
*/

```

--- 
    - Open the `style.css` file in a text editor and add the following code:

```
<?php
// Enqueue parent theme styles
function child_theme_enqueue_styles() {
    wp_enqueue_style('parent-style', get_template_directory_uri() . '/style.css');
}
add_action('wp_enqueue_scripts', 'child_theme_enqueue_styles');

```

---
### 5. Activate the Child Theme

1. **Upload Your Child Theme**:
    
    - If you created the child theme locally, compress the folder into a `.zip` file and upload it via **Appearance > Themes > Add New** in the WordPress dashboard.
2. **Activate the Child Theme**:
    
    - In the WordPress dashboard, go to **Appearance > Themes**.
    - Locate your child theme and click **Activate**.

## Modify the Template File

- WooCommerce templates can be overridden in your theme.
- Copy the `single-product.php` file from the `woocommerce/templates/` directory to your child theme in `your-theme-child/woocommerce/single-product.php`.

---

### 3. Insert the Checkout Form

- Open the copied `single-product.php` file and locate where you want the checkout form to appear.
- Add the WooCommerce checkout shortcode: 
	- echo do_shortcode('[woocommerce_checkout]');
