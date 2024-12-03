## CSS variables

DM Editor has built in css variables which is useful to support full width in widget.

| Name                    | Edit value            | view value               | Example                                                                                                                                      |
| ----------------------- | --------------------- | ------------------------ | -------------------------------------------------------------------------------------------------------------------------------------------- |
| `--dme-container-width` | Override by DM Editor | Set by project developer | `--dme-container-width: 1200px`, `100vw` - full screen width (remember to use over-flow-x: hidden for body because 100vw includes scrollbar) |
| `--dme-main-width`      | Override by DM Editor | Set by project developer | `--dme-main-width: 960px`, `var(--dme-container-width)` - same as container width.                                                           |

!!! note "Note"

    When switching to mobil/tablet, those values need to be changed also.

## CSS Classes

| Name                                                       | Explaination                                                                                                                                                                         |
| ---------------------------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ |
| `dmeditor-view `                                           | Class in root div of DM Editor                                                                                                                                                       |
| `dme-viewmode-mobile`, `dme-viewmode-tablet`               | Same div in `dmeditor-view`, in mobile or tablet mode. <br /> Recommaned to set `--dme-container-width` and `--dme-main-width` under these classes, because it will work in preview. |
| `dme-block`                                                | In root div on all widget blocks.                                                                                                                                                    |
| `dme-block-depth-1` where 1 is the depth                   | Level of blocks(starting from 1). Same node of `dme-block`                                                                                                                           |
| `dme-blocktype-image` where image is the widget identifier | Class identifier for the widget. Same node of `dme-block`                                                                                                                            |
