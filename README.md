## Wordpress Documentation

Все, что находится вне пары открывающегося и закрывающегося тегов, игнорируется интерпретатором PHP, у которого есть возможность обрабатывать файлы со смешанным содержимым. Это позволяет PHP-коду быть встроенным в документы HTML, к примеру, для создания шаблонов.

### Markdown

Markdown is a lightweight and easy-to-use syntax for styling your writing. It includes conventions for

```markdown
if ( function_exists( 'has_nav_menu' ) && has_nav_menu( 'main-menu' ) ) {
  wp_nav_menu( array(
    'depth' => 6,
    'sort_column' => 'menu_order',
    'container' => 'ul',
    'menu_class' => 'nav',
    'menu_id' => false,
    'theme_location' => 'main-menu'
  ) );
} else {

}
```
Добавление id категории поста в body_class
```markdown
function category_id_class( $classes ) {
  global $post;
  
  foreach( get_the_category( $post->ID ) as $category ) {
    $classes[] = 'id' . $category->term_id;
  }
  
  return $classes;
}

add_filter('post_class', 'category_id_class');
add_filter('body_class', 'category_id_class');
```
```markdown
$categories = get_the_category();

if( $categories ) {
  foreach( $categories as $category ) {
    $out . = 'categoryid-'. $category->term_id . '';
  }
  
  echo trim( $out, ', ' );
} 
```
```markdown
// For your functions.php file or a functionality plugin:

function cc_mime_types( $mimes ) {
  $mimes['svg'] = 'image/svg+xml';
  return $mimes;
}

add_filter( 'upload_mimes', 'cc_mime_types' );

function fix_svg_thumb_display() {
  echo '
    td.media-icon img[src$=".svg"], img[src$=".svg"].attachment-post-thumbnail { 
      width: 100% !important; 
      height: auto !important; 
    }
  ';
}

add_action( 'admin_head', 'fix_svg_thumb_display' );
```
```markdown
if ( has_post_format( 'link' ) ) {
  the_content();
} else {
  the_excerpt();
}
```
```markdown
if ( is_user_logged_in() ) {
  
} else {

}
```
```markdown
// Customize mce editor font sizes
if ( ! function_exists( 'wpex_mce_text_sizes' ) ) {
  function wpex_mce_text_sizes( $initArray ) {
    $initArray['fontsize_formats'] = '9px 10px 12px 13px 14px 16px 18px 21px 24px 28px 32px 36px';
    return $initArray;
  }
}

add_filter( 'tiny_mce_before_init', 'wpex_mce_text_sizes' );
```
```markdown
Syntax highlighted code block

# Header 1
## Header 2
### Header 3

- Bulleted
- List

1. Numbered
2. List

**Bold** and _Italic_ and `Code` text

[Link](url) and ![Image](src)
```

For more details see [GitHub Flavored Markdown](https://guides.github.com/features/mastering-markdown/).

### Jekyll Themes

Your Pages site will use the layout and styles from the Jekyll theme you have selected in your [repository settings](https://github.com/vovagabel/wpdock/settings). The name of this theme is saved in the Jekyll `_config.yml` configuration file.

### Support or Contact

Having trouble with Pages? Check out our [documentation](https://help.github.com/categories/github-pages-basics/) or [contact support](https://github.com/contact) and we’ll help you sort it out.
