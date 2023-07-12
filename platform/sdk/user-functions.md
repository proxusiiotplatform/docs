# Proxus SDK - User Functions Documentation

The Proxus SDK provides a comprehensive set of tools and features for developing user functions within the Proxus IIoT platform. This documentation will guide you through the working mechanism and various aspects of the Proxus SDK.

## Table of Contents

1\. [Introduction](#introduction)

2\. [FunctionBase Class](#functionbase-class)

3\. [SubscriptionContext Class](#subscriptioncontext-class)

4\. [FunctionContext Class](#functioncontext-class)

5\. [Working Mechanism](#working-mechanism)

6\. [Event Handling](#event-handling)

7\. [Database Interaction](#database-interaction)

8\. [Logging](#logging)

9\. [Examples](#examples)

## Introduction

The Proxus SDK allows developers to create custom user functions that enhance the functionality of the Proxus IIoT platform. User functions are implemented by extending the `FunctionBase` class provided by the SDK.

## FunctionBase Class

The `FunctionBase` class serves as the base class for all user functions in the Proxus SDK. It provides a wide range of methods, properties, and functionality that can be utilized within your user functions. Key features of the `FunctionBase` class include:

- **SystemEventStream**: An event stream used for publishing and subscribing to events within the Proxus system.
- **Logger**: An optional logging component for recording messages and events.
- **ActorId**: A property representing the unique ID of the actor executing the user function.
- **Subscriptions**: A collection of subscription contexts used for managing event subscriptions.
- **OnMessageReceive**: A method that can be overridden to handle incoming messages.
- **Publish**: A method for publishing events to the event stream.
- **SaveToDB**: A method for saving data to the database.
- **OnStopping**: A method called when the actor executing the user function is stopping.
- **OnStarted**: A method called when the actor executing the user function is started.
- **SendRepeatedly**: A method for scheduling repeated message sending.
- **ExecuteQueryAndTransformResult**: A method for executing database queries and transforming the results.
- **ExecuteQuery**: A method for executing database queries and returning formatted results.
- **LogInformation/LogWarning/LogCritical/LogError/LogTrace/LogDebug**: Logging methods for different log levels.

## SubscriptionContext Class

The `SubscriptionContext` class represents a subscription context within the Proxus system. It encapsulates the details of an event subscription, including the type of the event and the topics to filter the events. The `SubscriptionContext` class contains the following properties:

- **Type**: The type of the event to subscribe to.
- **Topics**: A set of topics used to filter the events.
- **Subscription**: The subscription object returned when subscribing to the event stream.

## FunctionContext Class

The `FunctionContext` class provides contextual information about a user function execution. It contains details such as the type of the message received, the topic of the message, the sender's ID, and the message itself. The `FunctionContext` class includes the following properties:

- **Type**: The type of the message received.
- **Topic**: The topic associated with the message.
- **SenderId**: The ID of the sender of the message.
- **SenderRequestId**: The request ID of the sender of the message.
- **SenderAddress**: The address of the sender of the message.
- **Message**: The message received.

## Working Mechanism

The Proxus SDK user functions are executed within actors, which are lightweight concurrent execution units. When a user function is executed, the `ReceiveAsync` method of the `FunctionBase` class is invoked, and the user function logic can be implemented within the `OnMessageReceive` method. The execution flow and lifecycle of a user function are managed by the Proxus runtime.

## Event Handling

User functions can subscribe to events using the event stream provided by the Proxus system. By defining subscription contexts and registering them in the `OnStarted` method, user functions can receive and handle specific events. The `OnMessageReceive` method is responsible for processing the received messages based on the defined subscriptions and message types.

## Database Interaction

The Proxus SDK allows user functions to interact with databases using the XPO framework. User functions can execute database queries, transform query results, and save data to the database. The `ExecuteQueryAndTransformResult` method and `ExecuteQuery` method provide convenient ways to perform database operations within user functions.

## Logging

User functions can utilize the logging functionality provided by the Proxus SDK. The `Logger` property allows user functions to log messages at different log levels, such as information, warning, error, and debug. The logging methods can be used to record important events and information during the execution of user functions.

## Lifecycle Management

The lifecycle of a user function, including initialization and termination, is managed by the Proxus runtime. When a user function is started, the `Started` message is received, and the `OnStarted` method is called. Similarly, when a user function is stopped, the `Stopping` message is received, and the `OnStopping` method is called. User functions can perform initialization tasks in the `OnStarted` method and cleanup tasks in the `OnStopping` method.

## Examples

Here are some examples to illustrate the usage of the Proxus SDK user functions:

```csharp

// Example 1: Creating a custom user function

using Proxus.SDK;

public class MyFunction : FunctionBase {

    protected override void OnMessageReceive(FunctionContext ctx) {

        // Handle incoming messages here

        if (ctx.Message is MyCustomMessage message) {

            // Do something with the message

        }

    }

}

// Example 2: Subscribing to events in the OnStarted method

protected override void OnStarted() {

    // Subscribe to specific events

    Subscriptions.Add(new SubscriptionContext {

        Type = typeof(MyEvent),

        Topics = new HashSet<string> { "Topic1", "Topic2" }

    });

}

// Example 3: Publishing an event

protected void PublishEvent() {

    var myEvent = new MyEvent();

    Publish(myEvent);

}

// Example 4: Saving data to the database

protected void SaveData() {

    var data = new TransportData();

    SaveToDB(data);

}
```
