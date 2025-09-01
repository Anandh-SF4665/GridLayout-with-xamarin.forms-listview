# GridLayout with xamarin.forms listview
This sample show case the grid layout in listview xamarin.forms

## Sample

```xaml
<Grid>
    <syncfusion:SfListView x:Name="listView"
                    SelectionMode="Multiple"
                    Grid.Row="1"                              
                    SelectedItems="{Binding SelectedItems}"
                    ItemSpacing="3">

        <syncfusion:SfListView.ItemTemplate>
            <DataTemplate>
                <Grid RowSpacing="0" ColumnSpacing="0">
                    . . . 
                    . . .
                </Grid>
            </DataTemplate>
        </syncfusion:SfListView.ItemTemplate>
</Grid>

C#:
protected override void OnSizeAllocated(double width, double height)
{
    base.OnSizeAllocated(width, height);
    try
    {
        base.OnSizeAllocated(width, height);

        if (width > 0 && pageWidth != width)
        {
            var size = Application.Current.MainPage.Width / listView.ItemSize;
            var gridLayout = listView.LayoutManager as GridLayout;
            gridLayout.SpanCount = (int)size;                  
            listView.LayoutManager = gridLayout;
        }
    }
    catch (Exception ex)
    {

    }
}
```
## Requirements to run the demo

* Xamarin add-ons for Visual Studio (available via the Visual Studio installer).

## Troubleshooting

### Path too long exception

If you are facing path too long exception when building this example project, close Visual Studio and rename the repository to short and build the project.
