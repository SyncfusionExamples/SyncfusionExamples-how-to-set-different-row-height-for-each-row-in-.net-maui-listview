# SyncfusionExamples-how-to-set-different-row-height-for-each-row-in-.net-maui-listview

This example demonstrates how to set different row height for each row .NET MAUI ListView (SfListView).

## Sample

```xaml
<sfListView:SfListView x:Name="listView"  
                                ItemSpacing="5" 
                                ItemsSource="{Binding Items}" 
                                SelectionMode="Multiple"
                                AutoFitMode="DynamicHeight">
    <sfListView:SfListView.ItemTemplate>
        <DataTemplate>
            <Grid x:Name="grid">
                <Grid.RowDefinitions>
                    <RowDefinition Height="*" />
                    <RowDefinition Height="*" />
                </Grid.RowDefinitions>
                <Label  Grid.Row="0" HorizontalTextAlignment="Center" HorizontalOptions="StartAndExpand" Text="{Binding ContactName}" FontSize="18" />
                <Label Grid.Row="1" HorizontalTextAlignment="Center" HorizontalOptions="StartAndExpand"  Text="{Binding ContactNumber}" FontSize="15" />
            </Grid>
        </DataTemplate>
    </sfListView:SfListView.ItemTemplate>
</sfListView:SfListView>
```

```c#
listView.QueryItemSize += ListView_QueryItemSize;

private void ListView_QueryItemSize(object sender, QueryItemSizeEventArgs e)
{
    if (e.ItemIndex % 2 == 0)
        e.ItemSize = 50;
    else
        e.ItemSize = 100;
    e.Handled = true;
}

```

## Requirements to run the demo

* [Visual Studio 2017](https://visualstudio.microsoft.com/downloads/) or [Visual Studio for Mac](https://visualstudio.microsoft.com/vs/mac/)
* Xamarin add-ons for Visual Studio (available via the Visual Studio installer).

## Troubleshooting

### Path too long exception

If you are facing path too long exception when building this example project, close Visual Studio and rename the repository to short and build the project.
