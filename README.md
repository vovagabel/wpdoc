## Wordpress Documentation

You can use the [editor on GitHub](https://github.com/vovagabel/wpdock/edit/master/README.md) to maintain and preview the content for your website in Markdown files.

Whenever you commit to this repository, GitHub Pages will run [Jekyll](https://jekyllrb.com/) to rebuild the pages in your site, from the content in your Markdown files.

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
