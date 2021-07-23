# CarbManager Flutter Assignment

<img src=".github/assignment_preview.png" width="350">

## Getting Started

We will use a free API service called [Finnhub](https://finnhub.io/); it is necessary to generate your API Key for this purpose.

**But it isn't necessary to share it.**

## Recommendations

**About your process**

If the assignment outcome will be shared in a git versioned repository, it is recommended to share its progress through commit history. This helps us get to know your process.

**About the project design strategy**

You can use your own _(MVC, MVP, MVVM, etc)_. It is good to start easy and then make the refinements to reach your desired structure and outcome.

**About the state management**

You can choose any of them _(Lift state, ChangeNotifier, provider, BLoC, bloc, rxDart, etc)_, this assignment might not be the best case to implement any of them, but it shouldn't hold you from showing your beloved states.

## Explanation

The assignment is about providing a two-way communication between the app and a provided `html` file mounted inside a webview.

We will be connecting to the [Websocket Trades](https://finnhub.io/docs/api/websocket-trades) service from Finnhub, and send the retrieved Stock updates from the application to the webview.

## Sequence Diagram

<img src=".github/assignment_sequence.png" width="500">

## Step by step

- Store all app strings in clean way of your choice
- Add a MaterialApp with an appBar with the following title: "CM Flutter Assignment"
- Setup a webview to load the html file located in `/assets/app.html`
- Create a channel called `appMessageHandler` to receive messages from the website
- Add support for sending messages to the website through `nativeMessageHandler` function. It receives the following argument:
```
  nativeMessageHandler([
    {
      lastPrice: num;
      name: string;
      timestamp: DateFormat('MM/dd/yyyy - hh:mm a');
      volume: num;
    }
  ]);
```
- Setup and connect to `wss://ws.finnhub.io` websocket, providing it a configurable token (https://finnhub.io/docs/api/websocket-trades)
- Subscribe to a minimum of 5 symbols (you can search symbols here https://finnhub.io/docs/api/symbol-search)
- Listen to messages and send updates to the webview
- Add support for closing the websocket on app lifecycle

## Improvements

The following steps are not required to complete the assignment but add some value:

- Add a Floating Action Button with a refresh icon, whenever it is actioned it will send updates to the webview, meaning that all the updates will be stored in the app until the button is hit.
- Move the socket listening to a new isolate, and send data only when the Action button is hit.


