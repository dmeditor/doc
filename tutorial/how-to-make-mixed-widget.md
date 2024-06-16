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

### Rendering children

There are 2 components which can be used for rendering children:

```javascript
<BlockRender mode={mode} data={} path={} />

<BlockListRender mode={mode} blockData={} path={} allowedTypes={} />
```

In most cases `BlockRender` is good enough. If you want to render a list directly(not using `list` widget), you can use `BlockListRender`. Eg. In Tabs/Accordion, a tab/accordion item can use `BlockListRender` to avoid unncessary `list` block as parent for content blocks in a tab.

### Child settings

