# How to set different row height for each row in .NET MAUI ListView (SfListView)?

The [.NET MAUI ListView](https://www.syncfusion.com/maui-controls/maui-listview) allows you to customize the row height for each item by utilizing the [QueryItemSize](https://help.syncfusion.com/cr/maui/Syncfusion.Maui.ListView.SfListView.html#Syncfusion_Maui_ListView_SfListView_QueryItemSize) event. This event is triggered whenever an item comes into view, with the [QueryItemSizeEventArgs](https://help.syncfusion.com/cr/maui/Syncfusion.Maui.ListView.QueryItemSizeEventArgs.html) argument providing relevant information, including item index, size, and a handled bool.

**XAML:**
```
<ContentPage xmlns:sfListView="clr-namespace:Syncfusion.Maui.ListView;assembly=Syncfusion.Maui.ListView">

    <ContentPage.BindingContext>
        <local:ContactsViewModel x:Name="viewModel"/>
    </ContentPage.BindingContext>

    <Grid>
        <sfListView:SfListView    x:Name="listView"  
                                  ItemSpacing="5" 
                                  ItemsSource="{Binding Items}" 
                                  SelectionMode="Multiple">
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
    </Grid>
</ContentPage>
```

**C# :**
```
public partial class MainPage : ContentPage
{
    public MainPage()
    {
        InitializeComponent();
        listView.QueryItemSize += ListView_QueryItemSize;
    }

    private void ListView_QueryItemSize(object sender, QueryItemSizeEventArgs e)
    {
        if (e.ItemIndex % 2 == 0)
            e.ItemSize = 50;
        else
            e.ItemSize = 100;
        e.Handled = true;
    }
}
```

**Output:**
 
 ![QueryItemSize.PNG](https://support.syncfusion.com/kb/attachment/article/14879/inline?token=eyJhbGciOiJodHRwOi8vd3d3LnczLm9yZy8yMDAxLzA0L3htbGRzaWctbW9yZSNobWFjLXNoYTI1NiIsInR5cCI6IkpXVCJ9.eyJpZCI6IjE2NjkwIiwib3JnaWQiOiIzIiwiaXNzIjoic3VwcG9ydC5zeW5jZnVzaW9uLmNvbSJ9.J3415SLT64f2utetfUdXSQHZRf1Ov1X6IFJCHPddr_w)

**Conclusion**

I hope you enjoyed learning how to set different row heights for each row in .NET MAUI ListView.

You can refer to our [.NET MAUI ListView feature tour](https://www.syncfusion.com/maui-controls/maui-listview) page to know about its other groundbreaking feature representations and [documentation](https://help.syncfusion.com/maui/listview/getting-started), and how to quickly get started with configuration specifications. You can also explore our [.NET MAUI ListView example](https://github.com/syncfusion/maui-demos/tree/master/MAUI/ListView) to understand how to create and manipulate data.

You can check out our components from the [License and Downloads](https://www.syncfusion.com/sales/teamlicense) page for current customers. If you are new to Syncfusion®, try our 30-day [free trial](https://www.syncfusion.com/downloads/maui/confirm) to check out our other controls.

Please let us know in the comments section below if you have any queries or require clarification. You can also contact us through our [support forums](https://www.syncfusion.com/forums), [Direct-Trac](https://support.syncfusion.com/create), or [feedback portal](https://www.syncfusion.com/feedback/maui?control=sflistview). We are always happy to assist you!
