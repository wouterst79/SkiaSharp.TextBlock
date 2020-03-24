# SkiaSharp.TextBlock
SkiaSharp.TextBlock adds text block and rich text layout to SkiaSharp 

## Sample uses:
NOTE: DrawTextBlock returns the SKRect that contains the text. The sample project draws a green box around this rect. See the [source](./samples) for details.

### basic samples
![basic samples-Hello World](./samples/output/basic%20samples-Hello%20World.png)
```C#
canvas.DrawTextBlock("Hello world!", new SKRect(0, 0, 100, 0), new FLFont(14), SKColors.Black);
```

![basic samples-FlowDirection.RightToLeft](./samples/output/basic%20samples-FlowDirection.RightToLeft.png)
```C#
var text = new Text(new FLFont(14), SKColors.Black, "Hello world!");
canvas.DrawTextBlock(text, new SKRect(0, 0, 100, 0), null, FlowDirection.RightToLeft);
```

![basic samples-Word Wrap](./samples/output/basic%20samples-Word%20Wrap.png)
```C#
var text = new Text(new FLFont(14), SKColors.Black, "Hello world!");
return canvas.DrawTextBlock(text, new SKRect(0, 0, 50, 0));
```

![basic samples-LineBreakMode.Center](./samples/output/basic%20samples-LineBreakMode.Center.png)
```C#
var text = new Text(new FLFont(14), SKColors.Black, "Hello world!", LineBreakMode.Center);
return canvas.DrawTextBlock(text, new SKRect(0, 0, 50, 0));
```

![basic samples-LineBreakMode.MiddleTruncation](./samples/output/basic%20samples-LineBreakMode.MiddleTruncation.png)
```C#
var text = new Text(new FLFont(14), SKColors.Black, "Hello world!", LineBreakMode.MiddleTruncation);
return canvas.DrawTextBlock(text, new SKRect(0, 0, 50, 0));
```

### word wrap
![animated](./samples/output/animated.gif)
![animated](./samples/output/animated%20rtl.gif)

### basic samples 2
![basic samples 2-Word Wrap - Tight](./samples/output/basic%20samples%202-Word%20Wrap%20-%20Tight.png)
```C#
var text = new Text(new FLFont(14), SKColors.Black, "Hello world!");
return canvas.DrawTextBlock(text, new SKRect(0, 0, 20, 0));
```

![basic samples 2-Courier New](./samples/output/basic%20samples%202-Courier%20New.png)
```C#
var text = new Text(new FLFont("Courier New", 14), SKColors.Black, "Hello world!");
return canvas.DrawTextBlock(text, new SKRect(0, 0, 100, 0));
```

![basic samples 2-Color and Size](./samples/output/basic%20samples%202-Color%20and%20Size.png)
```C#
var text = new Text(new FLFont(20), SKColors.Red, "Hello world!");
return canvas.DrawTextBlock(text, new SKRect(0, 0, 100, 0)); 
```

![basic samples 2-New line](./samples/output/basic%20samples%202-New%20line.png)
```C#
var text = new Text(new FLFont(14), SKColors.Black, @"
(leading) new- line support...

Hello World!
SkiaSharp Rocks!");
return canvas.DrawTextBlock(text, new SKRect(0, 0, 150, 0));
```

![basic samples 2-New Line - Trailing](./samples/output/basic%20samples%202-New%20Line%20-%20Trailing.png)
```C#
var text = new Text(new FLFont(14), SKColors.Black, @"Trailing new- line support:

");
return canvas.DrawTextBlock(text, new SKRect(0, 0, 150, 0));
```

### typeface detection
![typeface detection-Typeface Detection - Non-latin](./samples/output/typeface%20detection-Typeface%20Detection%20-%20Non-latin.png)
```C#
var text = new Text(new FLFont(14), SKColors.Black, "年");
return canvas.DrawTextBlock(text, new SKRect(0, 0, 100, 0));
```

![typeface detection-Typeface Detection - Symbols](./samples/output/typeface%20detection-Typeface%20Detection%20-%20Symbols.png)
```C#
var text = new Text(new FLFont(14), SKColors.Black, "↺");
return canvas.DrawTextBlock(text, new SKRect(0, 0, 100, 0));
```

![typeface detection-Unicode](./samples/output/typeface%20detection-Unicode.png)
```C#
var text = new Text(new FLFont(14), SKColors.Black, "🌐🍪🍕🚀");
return canvas.DrawTextBlock(text, new SKRect(0, 0, 100, 0));
```

![typeface detection-Rtl Support](./samples/output/typeface%20detection-Rtl%20Support.png)
```C#
var text = new Text(new FLFont(14), SKColors.Black, "مرحبا بالعالم");
return canvas.DrawTextBlock(text, new SKRect(0, 0, 100, 0), null, FlowDirection.RightToLeft);
```

![typeface detection-Rtl Word Wrap](./samples/output/typeface%20detection-Rtl%20Word%20Wrap.png)
```C#
var text = new Text(new FLFont(14), SKColors.Black, "مرحبا بالعالم");
return canvas.DrawTextBlock(text, new SKRect(50, 0, 100, 0), null, FlowDirection.RightToLeft);
```

### rich text
![rich text-Rich Text](./samples/output/rich%20text-Rich%20Text.png)
```C#
var text = new RichText()
{
    Spans =
    {
        new Text(new FLFont(10), SKColors.Black, "Hello "),
        new Text(new FLFont(20, true), SKColors.Black, "world! "),
        new Text(new FLFont(16), SKColors.Green, "SkiaSharp Rocks!"),
    }
};
return canvas.DrawRichTextBlock(text, new SKRect(0, 0, 200, 0));

```

### rich text 2
![rich text 2-rich text 2](./samples/output/rich%20text%202-rich%20text%202.png)
```C#
var text = new RichText()
{
    Spans =
    {
        new Text(new FLFont(16), SKColors.Green, "SkiaSharp Rocks!"),
        new Text(new FLFont(10), SKColors.Black, "Hello "),
        new Text(new FLFont(20, true), SKColors.Black, "world! "),
        new Text(new FLFont(14), SKColors.Black, @"Trailing new-line support:

"),
        new Text(new FLFont(16), SKColors.Green, "SkiaSharp Rocks!"),
        new Text(new FLFont(14), SKColors.Black, "مرحبا بالعالم"),
        new Text(new FLFont(16), SKColors.Green, "SkiaSharp Rocks!"),
        new Text(new FLFont(14), SKColors.Black, "年"),
        new Text(new FLFont(16), SKColors.Green, "SkiaSharp Rocks!"),
        new Text(new FLFont(14), SKColors.Black, "↺"),
    }
};
return canvas.DrawRichTextBlock(text, new SKRect(0, 0, 200, 0));
```

### lorum ipsum
![lorum ipsum-lorum ipsum](./samples/output/lorum%20ipsum-lorum%20ipsum.png)