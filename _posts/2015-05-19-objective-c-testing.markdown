---
layout: post
title:  "Testing With Objective C"
date:   2015-05-15 13:54:51
author: "KEVIN COLEMAN"
desc: "An introduction to testing frameworks and tools for iPhone development."
track: "179501785"
---

Building a blog has been very high on my list of todos for quite some time. I've attempted to build one in the past, but distractions have gotten in the way and I'd never quite completed the task. Over the past few weeks however, I've been able to dive into the Jekyll blogging framework and have finally whipped something together...the result of which you are currently reading ;).

![My helpful screenshot]({{ site.url }}/assets/hawks.jpg)

One of the things I would like to do on this blog is write technical posts from time to time that detail a new framework or technology that I have started using. This will force me to not only develop a more through understanding of said framework/technology, but will also hopefully benefit other readers. I have been the fortunate beneficiary of many such blog posts in the past and it is time to give back.

Given that I build this blog using Jekyll, I felt it only natural that I write the first technical post about the framework.

{% highlight objc %}
- (void)testToVerifyUserLogin
{
    XCTestExpectation *expectation = [self expectationWithDescription:@"Standard User Login Expectation"];
    NSMutableDictionary *credentials = [NSMutableDictionary new];
    [credentials setValue:@"test@gmail.com" forKey:SFAPIEmailKey];
    [credentials setValue:@"test_password" forKey:SFAPIPasswordKey];
    [credentials setValue:@"test_password" forKey:SFAPIConfirmationKey];

    [self.APImanager authenticateUserWithCredentials:credentials completion:^(NSString *accessToken, NSError *error){
        if (accessToken) {
            [expectation fulfill];
        }
    }];
    [self waitForCompletionWithTimeOut:5];
}
{% endhighlight %}

Check out the [Jekyll docs][jekyll] for more info on how to get the most out of Jekyll. File all bugs/feature requests at [Jekyll’s GitHub repo][jekyll-gh]. If you have questions, you can ask them on [Jekyll’s dedicated Help repository][jekyll-help].

[jekyll]:      http://jekyllrb.com
[jekyll-gh]:   https://github.com/jekyll/jekyll
[jekyll-help]: https://github.com/jekyll/jekyll-help
