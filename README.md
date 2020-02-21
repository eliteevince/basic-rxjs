# Basic RxJs
##	Overview

**R**eactive **E**xtensions for **J**ava**S**cript (**RxJS**) is a reactive streams library for reactive programming that allows you to work with asynchronous data streams. RxJS can be used both in the server-side using Node.js or the browser side using different libraries like Angular 2+, ReactJS etc.
## Why should we use RxJS over promises?

We may think that Promises are working fine why we should use RxJS. There are many advantages use of RxJS.

Many reasons are listed below such as error catching, cancellation, debouncing etc. That all are already available to Promises and callbacks. But they acquire more code complexity and additional libraries. 
###	Observables
-	If we use promises or something others we need to implement code that is run only once and success or fail.
-	Observables can be use when performing pure operation with changing argument or non-pure operations such as fetch data from server that might be change with time.
-	Observables are data streams, they can keep emitting values and any subscriptions will receive and process them separately at the time they each arrive.
-	If our action triggering multiple events, we can use RxJS.
-	In some situations, we want to update something reactively then we can use RxJS.

###	list of operators
-	In RxJS presents a lot of operators like Transformation operators, Filtering operators, Multicasting operators, Error handling operators etc.

###	Cancellation of subscriptions
-	In some framework when changes occur they recreate a component from scratch or mount and unmount component based on their visibility. Using Cancellation of subscriptions feature we can cancel all pending requests for those now non-existent components.

###	Error Catching
-	RxJS not only catch errors, they returning value to recover from them.

###	Retry on error
- RxJS provides us with the chance to retry on error.

The basic concepts you need should know about the RxJS as followed:
-	Observables
-	Observers
- Subscriptions
-	Operators
 
### Observables
Observables is a primitive type which is newly introduced and it’s acts as a blueprint for stream that how we want to create, subscribe to them, react to new values, and combine streams together to build new ones.

RxJS library gives us the Observable primitive.

Example 
```
// Import Observable from RxJs library
import {Observable} from 'rxjs';

// return value with observable
find(term:string): Observable<products[]> {
  let url = `${this.root}?id=${term}`;//api url
  return this.http.get(url);//return observable
}
```
### Observers
If you created the observable method or variable, To execute that method or variable and receiving notifications, you need to call its subscribe(), and passing an observer. 

Example
```
//Call server method find to get data
this.find(“1001”).subscribe(observer=>{
	console.log('Observer got a next value: ' + observer);
});
```

### Subscription
Subscription is basically use to execute the observable object. Subscription has a method which is unsubscribe. This method doesn’t take any parameters, just destroy all reference held by subscription.

Example
```
//Call server method find to get data
this.find(“1001”).subscribe(observer=>{
	console.log('Observer got a next value: ' + observer);
});
```
### Operators
RxJS contain operators also, operator is nothing but functions that we are call from RxJS object.

RxJS containing two kind of operator which is piping operator and creation operator.

Piping operators are a function, that are takes an Observable object as its input parameter and returns another Observable object.

Unlike Piping operators, Creation operators are a function that can be used for create an Observable object using joining with other Observable object or some common predefined behavior.

### Categories of operators
In RxJS there all operator has some categories like **Transformation operators, Filtering operators, Multicasting operators, Error handling operators** and **utility operators** etc.

**Transformation operator’s** category there are many operators present. Which is listed follow

**buffer, bufferCount, bufferTime, bufferToggle, concatMap, concatMapTo, exhaust, exhaustMap, expand, groupBy, map, mapTo, mergeMap, mergeMap, mergeScan, pairwise, partition, pluck, scan, switchMap, switchMapTo, window, windowCount, windowTime, windowToggle, windowWhen**

**Filtering operator’s** category listed below

**audit, auditTime, debounce, debounceTime, distinct, distinctKey, distinctUntilChanged, distinctUntilKeyChanged, elementAt, filter, first, ignoreElements, last, sample, sampleTime, single, skip, skipLast, skipUntil, skipWhile, take, takeLast, takeUntil,  takeWhile, throttle, throttleTime**

**Join operator’s** category listed below 

**combineAll, concatAll, exhaust, mergeAll, startWith, withLatestFrom**

**Multicasting operator’s** category listed below 

**multicast, publish, publishBehavior,  publishLast, publishReplay, share**

**Error Handling operator’s** category listed below 

**catchError, retry, retryWhen.**

**Utility operator’s** category listed below 
**tap, delay, delayWhen, dematerialize, materialize, observeOn, subscribeOn, timeInterval, timestamp, timeout, timeoutWith, toArray
Conditional and Boolean operator’s category listed below 
defaultIfEmpty, every, find, findIndex, isEmpty. 
Mathematical and Aggregate operator’s category listed below
count, max, min, reduce**

We can also create customize operators. For creating customize operator we can use pipe().

Example 
```
import {filter, map} from 'rxjs';
import {pipe} from 'rxjs';
function remove() {
  return pipe(
    filter(v => ! (v % 2)),
    map(v => v + v),
  );
}
```
