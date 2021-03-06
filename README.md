# JDStatusBarNotification

Show messages on top of the status bar. Customizable colors, font and animation. Supports progress display and can show an activity indicator. iOS 7 ready. iOS6 support. 

![Animation](gfx/animation.gif "Animation")

![Screenshots](gfx/screenshots.png "Screenshots")

## Installation

**Install via pods:**  
`pod 'JDStatusBarNotification'`

**Manually:**  

1. Drag the `JDStatusBarNotification/JDStatusBarNotification` folder into your project.
2. Add `#include "JDStatusBarNotification.h"`, where you want to use it

## Usage

JDStatusBarNotification is a singleton. You don't need to initialize it anywhere.
Just use the following class methods:

### Showing a notification

    + (UIView*)showWithStatus:(NSString *)status;
    + (UIView*)showWithStatus:(NSString *)status
                 dismissAfter:(NSTimeInterval)timeInterval;

The return value will be the notification view. You can just ignore it, but if you need further customization, this is where you can access the view.

### Dismissing a notification

    + (void)dismiss;
    + (void)dismissAfter:(NSTimeInterval)delay;
    
### Showing progress

![Progress animation](gfx/progress.gif "Progress animation")

    + (void)showProgress:(CGFloat)progress;  // Range: 0.0 - 1.0
    
### Showing activity

![Activity screenshot](gfx/activity.gif "Activity screenshot")

    + (void)showActivityIndicator:(BOOL)show
                   indicatorStyle:(UIActivityIndicatorViewStyle)style;
    
### Showing a notification with alternative styles

Available included styles:

- `JDStatusBarStyleDefault` (gray/gray)
- `JDStatusBarStyleDark` (black/white)
- `JDStatusBarStyleMatrix` (black/green)
- `JDStatusBarStyleError` (red/white)
- `JDStatusBarStyleWarning` (yellow/gray)
- `JDStatusBarStyleSuccess` (green/white)

Use them with the following methods:
               
    + (UIView*)showWithStatus:(NSString *)status
                    styleName:(NSString*)styleName;
                 
    + (UIView*)showWithStatus:(NSString *)status
                 dismissAfter:(NSTimeInterval)timeInterval
                    styleName:(NSString*)styleName;
                 
To present a notification using a custom style, use the `identifier` you specified in `addStyleNamed:prepare:`. See Customization below.

## Customization

    + (void)setDefaultStyle:(JDPrepareStyleBlock)prepareBlock;
    
    + (NSString*)addStyleNamed:(NSString*)identifier
                       prepare:(JDPrepareStyleBlock)prepareBlock;


The `prepareBlock` gives you a copy of the default style, which can be modified as you like:

	[JDStatusBarNotification addStyleNamed:<#identifier#>
	                               prepare:^JDStatusBarStyle*(JDStatusBarStyle *style) {
	                               
	                                   style.barColor = <#color#>;
	                                   style.textColor = <#color#>;
	                                   style.font = <#font#>;
	                                   
	                                   style.textShadow = <#shadow#>;
	                                   style.animationType = <#type#>;

                                       style.progressBarColor = <#color#>;
                                       style.progressBarHeight = <#height#>;
                                       style.progressBarPosition = <#position#>;

	                                   return style;
	                               }];


## Twitter

I'm [@jaydee3](http://twitter.com/jaydee3) on Twitter. Feel free to [post a tweet](https://twitter.com/intent/tweet?button_hashtag=JDStatusBarNotification&text=Simple%20and%20customizable%20statusbar%20notifications%20for%20iOS!%20Check%20it%20out.%20https://github.com/jaydee3/JDStatusBarNotification&via=jaydee3), if you like JDStatusBarNotification.  

[![TweetButton](gfx/tweetbutton.png "Tweet")](https://twitter.com/intent/tweet?button_hashtag=JDStatusBarNotification&text=Simple%20and%20customizable%20statusbar%20notifications%20for%20iOS!%20Check%20it%20out.%20https://github.com/jaydee3/JDStatusBarNotification&via=jaydee3)
