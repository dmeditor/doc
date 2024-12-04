# How to make a mixed widget

A mixed widget is widget containing other widget. Besides following [making a widget](./how-to-make-widget.md), there are extra configuration regarding child rendering and widget setting.

### Mixed widget data

It's recommaned to put all children blocks under property 'children', eg. Here is data example for Hero Text, where there is image on left and list on right.

⚠️ Note: It's important to keep order can disable deleting on the direct children(below are image and list), since this direct children strucutre is the 'schema' of mixed widget.

```javascript
{
        type: 'hero-text',
        data: {},
        children: [
          {
            id: nanoid(),
            type: 'image',
            isEmbed: true,
            data: {
              src: 'https://images.unsplash.com/photo-1561336313-0bd5e0b27ec8?q=80&w=2940&auto=format&fit=crop&ixlib=rb-4.0.3&ixid=M3wxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8fA%3D%3D',
              settings: {},
            },
          },
          {
            id: nanoid(),
            type: 'list',
            isEmbed: true,
            allowedTypes: ['heading', 'text', 'button'],
            data: { settings: { general: { padding: 10 } } },
            children: [
              {
                id: nanoid(),
                type: 'heading',
                isEmbed: true,
                data: {
                  value: 'Heading 2',
                  level: 2,
                },
              },
            ],
          },
        ],
      }
```

#### `isEmbed` should be `true` or `false`?

isEmbed should be true unless the parent is an gloabl container, eg. (a tab, an accordtion item) - some of container is embed also - eg. heading inside list of hero text. In general, if you want the element has no relation from the mixed widget(eg. element under a tab), it can be false, otherwise alway set to true, or if you want to treat the block part of the mixed widget or not.

DM Editor will automatically set `isEmbed` true if it's parent `list` widget is `true`.

### Rendering children

There are 2 components which can be used for rendering children:

```javascript
<BlockRender mode={mode} data={} path={} />

<BlockListRender mode={mode} blockData={} path={} allowedTypes={} />
```

In most cases `BlockRender` is good enough. If you want to render a list directly(not using `list` widget), you can use `BlockListRender`. Eg. In Tabs/Accordion, a tab/accordion item can use `BlockListRender` to avoid unncessary `list` block as parent for content blocks in a tab.

See [BlockRender & BlockListRender](../../reference/block-render) for detail.

### Children configuration

Mixed widget can control's embeded children's settings and styles.

In definition of the mixed widget, you can set rules by impelmenting below

```javascript
embedConfig?: {
        enabledSettings?: (
          settings: Array<Setting>,
          styles: { [key: string]: Array<string> },
          context: EmbedChildContext,
        ) => { settings: Array<Setting>; enabledStyles?: { [key: string]: Array<string> } };

        hasOwnView?: (context: EmbedChildContext) => boolean;
      };

```

Below example set only showing 'container' setting of image and list, and disable all styles dropdown of image and list. At same time, for all children under 'list', use it's own setting panel instead of embeded setting panel.

```javascript
embedConfig: {
      enabledSettings: (settings, styles, context) => {
        const settingResult = settings.filter((item) => {
          if (item.category !== 'block') {
            return true;
          } else {
            if (context.relativePath.length === 1) {
              if (context.relativePath[0] === 0) {
                //image
                if (!item.styleTags) {
                  return true;
                }
                return arrayHasCommonElement(item.styleTags, ['container']);
              } else {
                //list
                return item.styleTags?.includes('container');
              }
            }
            return true;
          }
        });
        let enabledStyles: any = {};
        //list elements
        if (context.relativePath.length === 2) {
          enabledStyles = undefined;
        }
        return { settings: settingResult, enabledStyles: enabledStyles };
      },
      hasOwnView: (context) => {
        if (context.relativePath.length >= 2 && context.relativePath[0] === 1) {
          return true;
        }
        return false;
      },
    },
```
