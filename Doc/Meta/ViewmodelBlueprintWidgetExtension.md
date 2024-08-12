# ViewmodelBlueprintWidgetExtension

Description: Function /Script/UMG.ListView:BP_SetListItems
Usage: UFUNCTION
Feature: Blueprint
Group: Widget Property
Type: string="abc"
Status: OnlyInternal

用来验证InListItems的Object类型是否符合EntryWidgetClass的MVVM绑定的ViewModelProperty。

当前只在ListView里该函数使用。

原理：

```cpp
UCLASS(meta = (EntryInterface = "/Script/UMG.UserObjectListEntry"), MinimalAPI)
class UListView : public UListViewBase, public ITypedUMGListView<UObject*>
{
	UFUNCTION(BlueprintCallable, Category = ListView, meta = (AllowPrivateAccess = true, DisplayName = "Set List Items", ViewmodelBlueprintWidgetExtension = "EntryViewModel"))
	UMG_API void BP_SetListItems(const TArray<UObject*>& InListItems);
}

void UMVVMViewBlueprintListViewBaseExtension::Precompile(UE::MVVM::Compiler::IMVVMBlueprintViewPrecompile* Compiler, UWidgetBlueprintGeneratedClass* Class)
{
}
```