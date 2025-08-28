# GridLayout with xamarin.forms listview
This sample show case the grid layout in listview xamarin.forms

## Sample

```xaml
<Grid>
    <Grid.RowDefinitions>
        <RowDefinition Height="Auto" />
        <RowDefinition Height="*" />
    </Grid.RowDefinitions>
    <Grid x:Name="headerGrid" BackgroundColor="#FFEEEEF2" HeightRequest="45">
        . . .
        . . .
    </Grid>
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

        <syncfusion:SfListView.GroupHeaderTemplate>
            <DataTemplate>
                <ViewCell>
                    <ViewCell.View>
                        <code>
                        . . .
                        . . .
                        <code>
                    </ViewCell.View>
                </ViewCell>
            </DataTemplate>
        </syncfusion:SfListView.GroupHeaderTemplate>
    </syncfusion:SfListView>
</Grid>

Code behind:
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
