---
excerpt: 分享一篇国外帖子，关于iOS的自动化测试的难点问题
layout: post
category : blog
tags: [XCUITest,iOS]
lang: zh
---

# Why XCUITest So Bad


分享一篇国外帖子，关于iOS的自动化测试的难点问题

[Why XCUITest So Bad](https://jon-gabilondo-angulo-7635.medium.com/why-is-xcuitest-so-bad-84917569e28b)

Conclusion I：
---
> Let’s start from the end, the conclusion. Just for the fun of breaking the usual order and saving you time.</br>
XCUITest does many things well. But there are some things it does badly. Being the only way to make UI Tests on iOS, any problem is going to be big. There are many systems to make UI tests but they all have to use XCUITest at the endpoint.</br>
If for any reason you are interested in getting a simple value such as the visibility of an UI element then you are headed to an unsatisfactory job. The reason is that “visibility” of an UI element is a very complicated matter. So much so that Apple doesn’t want to get involved in it. Therefore you will be alone in figuring out that “simple” property, condemned to write a ‘good enough’ solution that will need continuous refinements as you go along.</br>
You will find similar situations in the order of elements. Often, the order of elements as you traverse the UI Tree with the XCUITest API does not match what is represented in the screen. This can be a serious problem if you want to find the element that corresponds to a given X,Y on the screen. Again, finding an element by location X, Y is not something that Apple provides, therefore you need to use the XCUITest element traversing API to find the element.</br>
The conclusion is, stay away from using or figuring out the visibility and find element by X, Y in your UI tests, if you can.</br>
Are these complains about XCUITest APIs that are not available ? Yes and no. Read more if you are interested in more detailed information.
---

Conclusion II:
---
> I don’t think UI testing API in general should have fallen into complexities and uncertainties that make any request into anything but 100% accuracy. I think it is to add noise to engineering, waste of time, frustration. Specially not in a field that is all about elements in a tree with a clearly defined size position and visualisation properties.</br>
AI image based in testing accepts from the beginning that it is about percentage of accuracy, but the benefits are worth it.</br>
Errors of XCUITest in geometry and coordinates should not be acceptable, it is matter of being more precise in the calculations.</br>
Is there a solution to the visibility problem ? It may be a semantical problem, a mixup of the computing and human notion of visible. The computing notion of display, hidden and visible are very clear, no room for mistakes, the elements will be considered for mapping them onto the video memory or not, and simple clipping will do the rest. Will my eye see the element ? Well, that I can’t tell you. What are the values you added to opacity, stroke, what other elements are on top, what about their opacity. Can I click on them ? same response.</br>
The only party that could really know if something is visible, really, would be the GPU and the code that draws into the video memory. But the display engine is not and will not be built to keep a communication with the the testing engine to tell them how the painting went for every element.</br>
Particularly I would prefer a reliable API to know the element bounds to know if is within the screen. The visibility/display should be constrained whether it is meant to be painted on screen.</br>
Of course what I’d really want is a better XCUITest with no mistakes in geometry and element order. And a visibility and hittable attribute that is 99.99% accurate. Apple is in a better position than us to solve this problem.</br>
---
