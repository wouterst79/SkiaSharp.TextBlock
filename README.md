# SkiaSharp.TextBlock
SkiaSharp.TextBlock adds text block and rich text layout to SkiaSharp 

## Sample uses:
NOTE: DrawTextBlock returns the SKRect that contains the text. The sample project draws a green box around this rect. See the [source](./samples) for details.

## Basic Samples
### Hello World:
![Basic Samples-Hello World](./samples/output/Basic%20Samples-Hello%20World.png)
```C#
canvas.DrawTextBlock("Hello world!", new SKRect(0, 0, 100, 0), new FLFont(14), SKColors.Black);
```

### FlowDirection.RightToLeft:
![Basic Samples-FlowDirection.RightToLeft](./samples/output/Basic%20Samples-FlowDirection.RightToLeft.png)
```C#
var text = new Text(new FLFont(14), SKColors.Black, "Hello world!");
canvas.DrawTextBlock(text, new SKRect(0, 0, 100, 0), null, FlowDirection.RightToLeft);
```

### Word Wrap:
![Basic Samples-Word Wrap](./samples/output/Basic%20Samples-Word%20Wrap.png)
```C#
var text = new Text(new FLFont(14), SKColors.Black, "Hello world!");
return canvas.DrawTextBlock(text, new SKRect(0, 0, 50, 0));
```

### LineBreakMode.Center:
![Basic Samples-LineBreakMode.Center](./samples/output/Basic%20Samples-LineBreakMode.Center.png)
```C#
var text = new Text(new FLFont(14), SKColors.Black, "Hello world!", LineBreakMode.Center);
return canvas.DrawTextBlock(text, new SKRect(0, 0, 50, 0));
```

### LineBreakMode.MiddleTruncation:
![Basic Samples-LineBreakMode.MiddleTruncation](./samples/output/Basic%20Samples-LineBreakMode.MiddleTruncation.png)
```C#
var text = new Text(new FLFont(14), SKColors.Black, "Hello world!", LineBreakMode.MiddleTruncation);
return canvas.DrawTextBlock(text, new SKRect(0, 0, 50, 0));
```

### Word Wrap
![animated](./samples/output/animated.gif)
![animated](./samples/output/animated%20rtl.gif)

## Basic Samples 2
### Word Wrap - Tight:
![Basic Samples 2-Word Wrap - Tight](./samples/output/Basic%20Samples%202-Word%20Wrap%20-%20Tight.png)
```C#
var text = new Text(new FLFont(14), SKColors.Black, "Hello world!");
return canvas.DrawTextBlock(text, new SKRect(0, 0, 20, 0));
```

### Courier New:
![Basic Samples 2-Courier New](./samples/output/Basic%20Samples%202-Courier%20New.png)
```C#
var text = new Text(new FLFont("Courier New", 14), SKColors.Black, "Hello world!");
return canvas.DrawTextBlock(text, new SKRect(0, 0, 100, 0));
```

### Color and Size:
![Basic Samples 2-Color and Size](./samples/output/Basic%20Samples%202-Color%20and%20Size.png)
```C#
var text = new Text(new FLFont(20), SKColors.Red, "Hello world!");
return canvas.DrawTextBlock(text, new SKRect(0, 0, 100, 0)); 
```

### New line:
![Basic Samples 2-New line](./samples/output/Basic%20Samples%202-New%20line.png)
```C#
var text = new Text(new FLFont(14), SKColors.Black, @"
(leading) new- line support...

Hello World!
SkiaSharp Rocks!");
return canvas.DrawTextBlock(text, new SKRect(0, 0, 150, 0));
```

### New Line - Trailing:
![Basic Samples 2-New Line - Trailing](./samples/output/Basic%20Samples%202-New%20Line%20-%20Trailing.png)
```C#
var text = new Text(new FLFont(14), SKColors.Black, @"Trailing new- line support:

");
return canvas.DrawTextBlock(text, new SKRect(0, 0, 150, 0));
```

## Typeface Detection
### Non-latin:
![Typeface Detection-Non-latin](./samples/output/Typeface%20Detection-Non-latin.png)
```C#
var text = new Text(new FLFont(14), SKColors.Black, "年");
return canvas.DrawTextBlock(text, new SKRect(0, 0, 100, 0));
```

### Symbols:
![Typeface Detection-Symbols](./samples/output/Typeface%20Detection-Symbols.png)
```C#
var text = new Text(new FLFont(14), SKColors.Black, "↺");
return canvas.DrawTextBlock(text, new SKRect(0, 0, 100, 0));
```

### Unicode:
![Typeface Detection-Unicode](./samples/output/Typeface%20Detection-Unicode.png)
```C#
var text = new Text(new FLFont(14), SKColors.Black, "🌐🍪🍕🚀");
return canvas.DrawTextBlock(text, new SKRect(0, 0, 100, 0));
```

### Rtl Support:
![Typeface Detection-Rtl Support](./samples/output/Typeface%20Detection-Rtl%20Support.png)
```C#
var text = new Text(new FLFont(14), SKColors.Black, "مرحبا بالعالم");
return canvas.DrawTextBlock(text, new SKRect(0, 0, 100, 0), null, FlowDirection.RightToLeft);
```

### Rtl Word Wrap:
![Typeface Detection-Rtl Word Wrap](./samples/output/Typeface%20Detection-Rtl%20Word%20Wrap.png)
```C#
var text = new Text(new FLFont(14), SKColors.Black, "مرحبا بالعالم");
return canvas.DrawTextBlock(text, new SKRect(50, 0, 100, 0), null, FlowDirection.RightToLeft);
```

## Rich Text
### Shorter:
![Rich Text-Shorter](./samples/output/Rich%20Text-Shorter.png)
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

### Longer:
![Rich Text-Longer](./samples/output/Rich%20Text-Longer.png)
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

## Lorum ipsum
![Lorum ipsum](./samples/output/Lorum%20ipsum.png)
