This article explains how to hide the selection indicator in [.NET MAUI TabView.](https://www.syncfusion.com/maui-controls/maui-tab-view) The selection indicator highlights the currently selected tab. If you need to hide this indicator, you can set the [IndicatorStrokeThickness](https://help.syncfusion.com/cr/maui/Syncfusion.Maui.TabView.SfTabView.html#Syncfusion_Maui_TabView_SfTabView_IndicatorStrokeThickness) property to 0.

Instead of using an indicator, you can highlight the selected tab by changing its [TextColor](https://help.syncfusion.com/cr/maui/Syncfusion.Maui.TabView.SfTabItem.html#Syncfusion_Maui_TabView_SfTabItem_TextColor) property using the `VisualStateManager`. The following example demonstrates how to achieve this:

```
<ContentPage.Resources>
    <Style TargetType="tabView:SfTabItem">
        <Setter Property="VisualStateManager.VisualStateGroups">
            <VisualStateGroupList>
                <VisualStateGroup>
                    <VisualState x:Name="Normal" >
                        <VisualState.Setters>
                            <Setter Property="TextColor" Value="Brown" />
                        </VisualState.Setters>
                    </VisualState>
                    <VisualState x:Name="Selected">
                        <VisualState.Setters>
                            <Setter Property="TextColor" Value="Green" />
                        </VisualState.Setters>
                    </VisualState>
                </VisualStateGroup>
            </VisualStateGroupList>
        </Setter>
    </Style>
</ContentPage.Resources>
<tabView:SfTabView x:Name="tabView" IndicatorStrokeThickness="0">
    <tabView:SfTabView.Items>
        <tabView:SfTabItem Header="Call" x:Name="callItem" ImageTextSpacing="3"
                     ImagePosition="Top" >
            <tabView:SfTabItem.ImageSource>
                <FontImageSource Glyph="&#xfeb6;" x:Name="call"
                                 Color="{Binding Source={x:Reference callItem},Path=TextColor}"
                             FontFamily="MaterialDesignIcons"/>
            </tabView:SfTabItem.ImageSource>
            <tabView:SfTabItem.Content>
                <ListView RowHeight="50">
                    <ListView.ItemsSource>
                        <x:Array Type="{x:Type x:String}">
                            <x:String>James</x:String>
                            <x:String>Richard</x:String>
                            <x:String>Michael</x:String>
                            <x:String>Alex</x:String>
                            <x:String>Clara</x:String>
                        </x:Array>
                    </ListView.ItemsSource>
                    <ListView.ItemTemplate>
                        <DataTemplate>
                            <ViewCell>
                                <Grid Margin="10,5">
                                    <Label VerticalOptions="Start"
                                           HorizontalOptions="Start"
                                           TextColor="#666666"
                                           FontSize="16"
                                           Text="{Binding}" />
                                </Grid>
                            </ViewCell>
                        </DataTemplate>
                    </ListView.ItemTemplate>
                </ListView>
            </tabView:SfTabItem.Content>
        </tabView:SfTabItem>
        <!-- Add TabItems -->
    </tabView:SfTabView.Items>
</tabView:SfTabView>
```

This customization is useful when you want a minimalistic design or if you are implementing a custom visual style for the selected tab.

**Output**

![TabView-Indicator.gif](https://support.syncfusion.com/kb/agent/attachment/article/19040/inline?token=eyJhbGciOiJodHRwOi8vd3d3LnczLm9yZy8yMDAxLzA0L3htbGRzaWctbW9yZSNobWFjLXNoYTI1NiIsInR5cCI6IkpXVCJ9.eyJpZCI6IjM1NDcxIiwib3JnaWQiOiIzIiwiaXNzIjoic3VwcG9ydC5zeW5jZnVzaW9uLmNvbSJ9.U2nHC_gQNjXzqNaPFs_eC1V_p9yLfbVOc9E34BIF3Nc)