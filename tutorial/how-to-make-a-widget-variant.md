How to make a widget variant
---------

A widget variant is "configured widget". These configuration includes eg. enabled settings, pre-define data, allowed child widget, styles.

An example is grid, a grid can add all types of widget in a grid, with '3 column article grid' which is a variant of article will only allow article inside, and fixed column 3(not changable because column setting is disabled).


### Register a variant
Here is an example of registering a variant "Article title", which is based on heading:

```javascript
registerWidgetVariant({
    widget: 'heading',
    identifier: 'article_title',
    name: 'Article title',
    enabledSettings: ['settings.color'],
    getDefaultData: () => {
      return {
        id: nanoid(),
        type: 'heading:article_title',
        data: { value: 'Article title', level: 3, settings: {color:'red'} },
      };
    },
  }

```

### Use variant identifier as widget
Widget variant can act similar to widget, just with identifier: \<widget identifier\>:\<variant identifer\>, 

When storing data, it be like:

```javascript
{type:'heading:article_title', ...}
```

When setting allowed child types

```javascript
{allowed_types:['heading:article_title', ...]}
```

### Balance between widget variant or new widget




