This article explains some concepts and priciple of using DM Editor and extending widgets or styles.

### Main idea

!!! quote

    The idea behind DM Editor is to have an editor where it is easy to develop and style widget within React ecosystem, in the end together with developer bring good user experience for page editing.

### Principle: developer controls

While DM Editor aims for flexibility and good editorial experience, when it comes to project, the project developer takes main controls, since developer knows the customer best and configure what to use, and also what NOT to use.

DM Editor's api ensures enough configurations.

### Concept: widget

Widget is a block with functions. It can be basic like image, form, or mixed widget like hero-text which consists of other widgets.

There are 3 types of widgets:

- basic widget: an atom widget
- list: a container, eg. list, grid
- mixed: eg. hero-text, layouts or other widet which consists of widget(s) and custom rendering.

### Concept: widget style

Widget style is core concept of DM Editor. The idea behind is that widget focuses on function, widget styles focus on display theme. Most of time in a website, using style should cover most of design theme.

!!! sample end "Sample: button styles"

     A button can have size (small, medium), color (primary, secondary, etc), outline (fill/outline), round (no, small round, all round). All of those can be defined in button styles.

     Button icon - before or after or both can be widget style also.

Below is how it looks with styles (color and icon):

<img src="../../assets/button-sample.png" width="560px">

<br />

Style (Color) selecting:

<img src="../../assets/button-colors.png" width="250px">

In addition, a widget style can set style settings (eg. padding) so editor can choose a style and adjust futher more in style settings.

### Benefits of widget way from component's pespective

#### Visual way of adding component

When using DM Editor, the component will be added in a visual way so editor can just see the result in edit mode.

#### Component with settings and additional widget blocks

If you already have a react component, you can simply wrap it into a widget. And sometimes there is a better way: wrap it into a widget, with possibility of mixing other widgets for configuration or display.

A simple example is a form component, which is already done, but you want a form title or success/error message editable, then the form title/message can be a Heading or Text widget.

### Widget development

#### Put css style out of widget implementation

If the widget has potential to have different themes, then it's recommanded that only function related css stays in the widget, theme related css better to be in `widget style` - even if it's called `Default style`.

Eg. Gallery, the image grid css can be in widget, while close button, previous, next can be in `widget style`.

#### Edit on left area or setting panel?

Short answer is it depends. DM Editor tries to make good editorial experience, so it supports both or hybrid. In some widget like Form, it's better to use left area, but some widget like Gallery, it's better to add image on right.

!!! tip "Edit first when implementing widget"

    Edit first is good principle - when implementing editing, also implement view (backend view/preview), then the same view will be used in frontend.

    In addition, you only need to use admin in dev mode, the frontend will look the same.

Below is an example of Bridge play widget where it uses button on right to trigger edit mode - it will be much mess if the whole edit mode is alway open.

When select block:

<img src="../../assets/widget-bridge-play-view.png" width="800px">

When click "Edit" button on setting panel:

<img src="../../assets/widget-bridge-play-edit.png" width="800px">

Frontend:

<img src="../../assets/widget-bridge-play-frontend.png" width="700px">

### Project architecture

#### Use DM Editor in both content and layout editing?

Since DM Editor can be embeded to a page, and DM Editor can embed other blocks into, page editing, page design, layout making can all be done in DM Editor - the limit is up to widget/style.

Here are typical senarios of using DM Editor:

1. Edit an article or page with input data.
2. Edit a page with section menu. You will need layout widget like "section menu", where you can bind data source from other pages. In this case DM Editor handles page's section menu route automatically. Eg. a "About us" page with section menu: "About", "History", "Contact".
3. Edit whole site layout. You need widgets for site menus, main area, footer etc. In this case you will need to map route to DM Editor since "Main area" widget will handle all pages. Most of time layout is in the project, so this way is not needed, but it's possible and this way gets benefit of editing footer/header in DM Editor. Note it should be only administator doing this.

!!! tip "Tip: both news list and news detail can be DM Editor pages"

    A news list page can be just a static DM Editor page, with NewsList widget inside.

    A news detail page can be a static DM Editor page with News Detail widget inside, while fetching data is done in the widget.

!!! tip "Tip: Benefit of putting News Detail into DM Editor"

    Comparing to routing to news detail directly: Editor/Administrator can set option visually or add more info, eg. adding general message above, then it affect all the news detail.

#### Tune editor's styling ability

DM Editor gives lots of style freedom to editor. For example,

- Almost all widgets have common style settings (can be disabled) like: background color, padding, margin top, self align, width.

- DM Editor has layout widget like 2 columns layout, Grid, List container, so editor can add lots of levels inside, eg. 3 columns layout -> 2 columns layout -> left image right text

This "too much" freedom in general gives flexiblity, but sometimes can create bad design. There are some ways to help:

- Configure default styles, so when a widget is added, default style is set (eg. heading's top margin).
- Disable some unneeded general style settings.
- Predefine colors, like text color, background color, default color.
- Save predefined blocks so editor can use directly.

!!! tip

    Make some guidline of UI, like color, padding, font size, etc (with samples) for editors. Of course, close work between designer and editor is always the best way.

#### Share code between admin and frontend

It's recommanded to share common DM Editor code between frontend (eg. a nextjs project) and admin project - monorepo. Otherwise you will need to copy code between the 2 projects.

The code includes below:

- Initial code
- Widgets
- Styles
- Project styles
