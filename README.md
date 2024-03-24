# AvaloniaHiDPI_Lib

Avalonia library for handling High DPI displays on Linux Wayland. Based on an awesome work of Herman Kirshin: https://github.com/HermanKirshin/LinuxDisplayScale/

# Usage
1) Grab **AvaloniaHiDPI.dll** from the Releases page: https://github.com/MinikPLayer/AvaloniaLinuxHiDPI_Lib/releases/latest
2) Add reference to **AvaloniaHiDPI.dll** in your project.
3) In **Program.cs** add "AvaloniaHiDPI.LinuxHiDPI.SetAutoDpiScaling();" to your Main() function before any Avalonia calls.

In short change:

    [STAThread]
    public static void Main(string[] args) => BuildAvaloniaApp()
        .StartWithClassicDesktopLifetime(args);

to:

    [STAThread]
    public static void Main(string[] args) {
        AvaloniaHiDPI.LinuxHiDPI.SetAutoDpiScaling();

        BuildAvaloniaApp().StartWithClassicDesktopLifetime(args);
    }

SetAutoDpiScaling() will automatically detect correct scaling values, then set correct environment variable value according to Avalonia Docs (https://github.com/AvaloniaUI/Avalonia/wiki/Configuring-X11-per-monitor-DPI).
