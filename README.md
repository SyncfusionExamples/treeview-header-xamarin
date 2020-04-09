# How to show header for Xamarin.Forms TreeView (SfTreeView)

You can show header for [SfTreeView](https://help.syncfusion.com/xamarin/treeview/overview?) in Xamarin.Forms by customizing the parent grid with label and SfTreeView.

You can also refer the following article.

https://www.syncfusion.com/kb/11376/how-to-show-header-for-xamarin-forms-treeview-sftreeview

**XAML**

Define Grid with Label as header for TreeView in first row and TreeView in second row.

``` xml
<ContentPage xmlns="http://xamarin.com/schemas/2014/forms"
             xmlns:x="http://schemas.microsoft.com/winfx/2009/xaml"
             xmlns:local="clr-namespace:TreeViewXamarin"
             xmlns:syncfusion="clr-namespace:Syncfusion.XForms.TreeView;assembly=Syncfusion.SfTreeView.XForms"
             x:Class="TreeViewXamarin.MainPage">
 
    <ContentPage.BindingContext>
        <local:FileManagerViewModel x:Name="viewModel"/>
    </ContentPage.BindingContext>
 
    <Grid>
        <Grid.RowDefinitions>
            <RowDefinition Height="40"/>
            <RowDefinition Height="*"/>
        </Grid.RowDefinitions>
        <Grid>
            <Label Margin="5" TextColor="Teal" FontAttributes="Bold" FontSize="Medium" HorizontalTextAlignment="Start" 
                   VerticalTextAlignment="Center">
                <Label.FormattedText>
                    <FormattedString>
                        <Span Text="Nodes Count: " TextColor="DarkOrange" />
                        <Span Text="{Binding NodeCount}" TextColor="Green"/>
                    </FormattedString>
                </Label.FormattedText>
            </Label>
        </Grid>
        <syncfusion:SfTreeView x:Name="treeView" ItemHeight="40" Grid.Row="1" Indentation="15" ExpanderWidth="40"
                              ChildPropertyName="SubFiles" ItemsSource="{Binding ImageNodeInfo}" AutoExpandMode="AllNodesExpanded">
                             
            <syncfusion:SfTreeView.ItemTemplate>
                <DataTemplate>
                    …
                </DataTemplate>
            </syncfusion:SfTreeView.ItemTemplate>
        </syncfusion:SfTreeView>
    </Grid>
</ContentPage>
```

**C#**

In ViewModel, header label is updated with node count.

``` c#
namespace TreeViewXamarin
{
    public class FileManagerViewModel
    {
        public FileManagerViewModel()
        {
          ...
        }
        public int NodeCount
        {
            get => ImageNodeInfo.Count();
        }
        ...
    }
}
```

**Output**

![TreeViewHeader](https://github.com/SyncfusionExamples/treeview-header-xamarin/blob/master/ScreenShots/TreeViewHeader.png)
