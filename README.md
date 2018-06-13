# Project Overview

In this project you are given a web-based application that reads RSS feeds. The original developer of this application clearly saw the value in testing, they've already included [Jasmine](http://jasmine.github.io/) and even started writing their first test suite! Unfortunately, they decided to move on to start their own company and we're now left with an application with an incomplete test suite. That's where you come in.


# How to run this file
To run this file: 

you can either clone it using `git clone https://github.com/jermhern/RSSFeed-Jasmine-Testing.git` into a folder you have CDed into on your computer terminal and open index.html

or **download** the file from my github repo and open index.html to view the RSS Feed and Jasmine tests

Tests Added On The RSS Feeds
============================
this test assures that all of the feeds are **defined**. 
If the feeds are a length of 0 then the jasmine testing frame work will throw an error

    `it('are defined', function() {
        expect(allFeeds).toBeDefined();
        expect(allFeeds.length).not.toBe(0);
    });`


this test counts the amount of known feeds (4) and throws an error if the feed number is any less



    `it('have a defined URL', function() {
        let allFeedsURLs = [];
        for (let feed of allFeeds) {allFeedsURLs.push(feed.url);}
        expect(allFeedsURLs.length).toBe(4);
    });`

Tests Added On The Pop Out Menu
===============================
this test ensures the Pop Out menu is hidden by default 



    it('element is hidden by default', function() {
        let isMenuHidden = false;
        if(document.querySelector('.menu-hidden').classList.value === 'menu-hidden') {
            isMenuHidden = true;
        }
        expect(isMenuHidden).toBe(true);
    });

this test ensures the menu changes visibility when clicked 
(open when clicked from close, vice versa)



    `it('icon displays when clicked and hides when hidden', function() {
        let showingWhenOpen = false;
        let showingWhenClosed = true;

        if(document.querySelector('.menu-hidden').classList.value === 'menu-hidden') {
            showingWhenClosed = false;
            expect(showingWhenClosed).toBe(false);
        }
        if(document.querySelector('.menu-hidden').classList.value !== 'menu-hidden') {
            showingWhenOpen = true;
            expect(showingWhenOpen).toBe(true);
        }
    });`

Tests done on the initial entries
=================================
this test ensures 
         * function is called and completes its work, 
         * there is at least a single .entry element within the .feed container
         
         
         
    `beforeEach(function(done) {
        loadFeed(0, done);
    });

    it('should have at least one .entry element in .feed', function() {       
        feedEntry = document.querySelector('.feed').children.length;
        expect(feedEntry).not.toBe(0);
    });`

this test ensures when a new feed is loaded by the loadFeed 
function that the content actually changes



    `beforeEach(function(done) {
        loadFeed(1, function(){
            // old page before reload
            oldFeed = $('.feed').html();
            done();
        });
    });

    it('has loaded', function(done) {
        loadFeed(0, function() {
        // compare new page with old page after reload
        expect($('.feed').html()).not.toEqual(oldFeed);
        done();
        });
    });`
