## Callbacks

Callbacks are used to extend DM Editor with backend system like CMS, your own project's backend.

```typescript
setDMEditorCallback({
     browseImage?: ComponentType<{
     value: BrowseImageCallbackParams;
     onChange: (value: BrowseImageCallbackParams) => void;
     multiple?: boolean;
  }>;
  browseLink?: ComponentType<{
    value: BrowseLinkCallbackParams;
    onChange: (value: BrowseLinkCallbackParams) => void;
  }>;
  canEditControl?: (block: DMEData.Block) => boolean;
  getSavedBlocks?: (widget: string) => Array<SavedBlockData>;
})

```

| Name           | Description                                                                                                                                                                                                                                            |
| -------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ |
| browseImage    | A component when user browse image. It's rendered inside a Browse tab in the popup                                                                                                                                                                     |
| browseLink     | A component when user browse link. It's rendered inside a Browse tab in the popup.                                                                                                                                                                     |
| canEditControl | If a block can be set edit control: view, edit (not including delete). Config `editor.enableEditControl` need to be `true` to use. You can put some role check here. eg. return all true for admin users, but only true for some type/level for editor |
| getSavedBlocks | return saved block daa                                                                                                                                                                                                                                 |
