# Firebase Realtime Database Race Condition

This repository demonstrates a race condition encountered when using Firebase's Realtime Database `onValue` listener.  The issue occurs when multiple clients update data concurrently, leading to inconsistencies in real-time updates.

The `bug.js` file showcases the problematic code, while `bugSolution.js` provides a solution that leverages transactions or server timestamps to ensure data consistency.

## Setup

1.  Clone this repository.
2.  Install Firebase:
    ```bash
    npm install firebase
    ```
3.  Configure your Firebase project (add your Firebase config to a file named `firebaseConfig.js`).
4.  Run `bug.js` and `bugSolution.js` to observe the behavior.

## Problem

The `onValue` listener may not update immediately when other clients write to the database, leading to stale data in the UI. This issue stems from the asynchronous nature of database operations and the potential for race conditions.

## Solution

The solution uses Firebase transactions to guarantee atomicity and prevent race conditions by ensuring that only one client changes the data at any given time, resolving the inconsistency and ensuring data integrity. An alternative is presented using server timestamps to enforce a reliable order of operations.