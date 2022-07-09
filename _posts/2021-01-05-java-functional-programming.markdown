---
layout: post
title:  "Functional programming using Java"
date:   2021-01-10 16:55:23 +0530
categories: Java
---

# Functional Programming in Java

This article is not supposed to be an introduction of Functional programming as it is a very vast subject. However I would like to keep it short and still give a quick intro of functional programming and how is Java doing there.
Some basic features of Functional programming:
  - It is an alternate programming approach to impertive programming. In imperative programming - we give low level instruction of how to do. In functional programming, we say what to do.
  - Program consists of higher order functions which can accept functions as arguments and can also return functions as return values !

Now below are the ways in which Java encourages functional programming style though in a somewhat limited way compared to pure functional languages:
  - Introduction of Lambdas. Lambdas are nothing but anonymous implementation of functional interfaces. Fuynctional interfaces
  - Introduction of streams to process / transform collections. So functional programming does not encourage to use loops etc. as they are imperative, rather a series of constructs.
  - Introduction of some popular functional interfaces which are as follows :
    - Function<T, V> : Has a method named apply(T) which accepts T as argument and return V 
    - Supplier<T> : Has a method get() which does not accept any argument but return T
    - Consumer<V> : Has a method accept(V) which accepts an argument V
    - Predicate<A, boolean> : Has a method test(A) which accepts A and returns boolean

Just look at the below example of a functional programming stype in Java and how concisely we have achieved this
{% highlight ruby %}
       Comparator<TweetMessage> tweetMessageComparatorByCreationTime = Comparator.comparing(TweetMessage::getLCreationTimeInEpoch);

        // First group the tweets by user and then sort the groups by user creation time
        Map<TweetAuthor, List<TweetMessage>> tweetListMapGroupedByAuthor =
                tweetMessageList.stream().
                        collect(Collectors.groupingBy(TweetMessage::getTweetAuthor)).
                        entrySet().
                        stream().
                        sorted(Comparator.comparing(p -> p.getKey().getLCreationTimeInEpoch())).
                        collect(toMap(Map.Entry::getKey, Map.Entry::getValue,(e1, e2) -> e2, LinkedHashMap::new));

        // Within each group, sort the messages by creation time
        tweetListMapGroupedByAuthor.values()
                .forEach(messageList -> messageList.sort(tweetMessageComparatorByCreationTime));
{% endhighlight %}
Just imagine writing this code in imperative style. Needless to mention that functional programming achieves very clean code.
