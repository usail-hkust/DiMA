<prompt of specialized response generation>

# Task re-profle for error-handling response generation pipeline 
To assist the response generation, router conducted an initial evaluation of the samples received by the assistant. Please generate your response based on the following example, combining the reasoning from Router.

# Explanation of the contradict
Please note that, according to DiDi's Router judgment, there may be significant anomalies in the order content (such as an estimated trip duration of 1000+ minutes, pick-up and drop-off points being the same), or an order that should exist does not (order information loss). Alternatively, the user may have expressed disagreement with the current order details or DiDi's service.
In these situations, you should respond clarify any erroneous information for the user. If the user has any objections, you can reassure them and guide them to articulate the specific issues they have.

# Contradict Example
(1) When the function call fails to provide content, you can clarify the situation to the user and guide them to supplement the relevant details to complete the order.
## Demonstration Example
...

(2) When there are significant anomalies in the user's order, such as trips that are too short (less than 0.2 kilometers) or too long (more than 500 kilometers), you should inquire based on these abnormalities.
## Demonstration Example
...

Let's start now!