# Notes on implementation of features


### Code to enable showing file extensions in Windows Explorer

``` 
using Microsoft.Win32;
namespace ShowHideExtensions
{
	class Program
	{
		static void Main()
		{
			RegistryKey key =
				Registry.CurrentUser.CreateSubKey(
				"Software\\Microsoft\\Windows\\CurrentVersion\\Explorer\\Advanced");
			if ((int)key.GetValue("HideFileExt") == 0)
			{
				key.SetValue("HideFileExt", 1);
			}
			else
			{
				key.SetValue("HideFileExt", 0);
			}
		}
	}
}
```