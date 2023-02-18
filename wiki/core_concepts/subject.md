
## Subject

Subject is a core concept in the Grams Governance system that enables the creation, testing, composition, deployment, and monitoring of smart contracts. In this page, we will provide a detailed overview of subjects, including their attributes, state, behavior, and how to use them through the Grams Desktop Application.

### Attributes of a Subject

A subject is a data structure that encapsulates a smart contract's logic, configuration, and state. The attributes of a subject include:

-   **Address**: The unique identifier of the subject on the IOTA tangle.
-   **Name**: The human-readable name of the subject.
-   **Code**: The smart contract's code, written in a Turing-complete programming language such as Rust, C++, or Solidity.
-   **Language**: The programming language used to write the subject's code.
-   **Creator**: The IOTA address of the subject's creator.
-   **Timestamp**: The time the subject was created.
-   **Status**: The current status of the subject, which can be one of the following: `draft`, `pending`, `approved`, `deployed`, `failed`.
-   **Dependencies**: The other subjects on which this subject depends on.
-   **Composition**: The composition of this subject with other subjects to form a more complex smart contract.
-   **Metadata**: Optional metadata for the subject, such as the description, version, and author.

### State of a Subject

A subject has an internal state that represents the current values of its variables and the contract's history. The state can be read and modified by the contract's code using a set of pre-defined functions called methods. The state of a subject is stored on the IOTA tangle and is immutable once it has been deployed.

### Behavior of a Subject

A subject's behavior is determined by its code, which is executed when specific conditions are met. The code is typically executed in response to an event, such as a user sending a transaction to the subject's address or a dependency subject executing its own code. The behavior of a subject can be tested locally before being deployed on the IOTA tangle.

### Using Subjects through Grams Desktop Application

The Grams Desktop Application provides a user-friendly interface for creating, testing, composing, deploying, and monitoring subjects. Here are the steps to create and deploy a new subject:

1.  Open the Grams Desktop Application and go to the Governance section.
2.  Click on the "Create New Subject" button.
3.  Enter the name, code, and metadata of the subject.
4.  Select the programming language for the subject's code.
5.  Define the methods for the subject.
6.  Test the subject's behavior using the built-in simulator.
7.  Compose the subject with other subjects to form a more complex smart contract.
8.  Deploy the subject to the IOTA tangle by signing a transaction and waiting for the transaction to be confirmed.
9.  Monitor the subject's status and events using the Grams Desktop Application.

The Grams Desktop Application provides a convenient and secure way to manage subjects, their composition and dependencies, and deploy and monitor them on the IOTA tangle. With subjects, developers can create complex smart contracts that are reliable, secure, and easy to test and deploy.
