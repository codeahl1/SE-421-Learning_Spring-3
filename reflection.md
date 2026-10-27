# Reflection — SE/CprE 4210: Learning Sprint #3, Problem 5

**Note:** This is an AI-assisted draft. Review and personalize it after running the app so the reflection accurately represents your own experience.

For this assignment, I built a small interactive web application covering hash-collision denial of service, regular-expression denial of service (ReDoS), and timing side-channel attacks from Module 5. I wanted to make the material more intuitive by allowing learners to change inputs and immediately observe how the modeled behavior changes.

The hash-table visualization made the distinction between typical and worst-case complexity more concrete. In the simplified model, distinct keys placed into different buckets need no equality comparisons, while intentionally colliding keys require progressively more comparisons. When all keys collide, the same insertion process requires progressively longer scans, and the total comparisons grow quadratically. In the ReDoS section, increasing the number of repeated characters shows how the number of possible partitions can double with each additional character. This helped connect catastrophic backtracking to exponential growth rather than just memorizing its definition. The timing section illustrates a different type of vulnerability: a system can return the same error message while still exposing information through differences in execution time.

My workflow was to use the lecture slides to identify suitable examples, ask AI to help design safe interactive demonstrations, and implement the result in a single HTML file with embedded CSS and JavaScript. I chose simple bounded simulations rather than executing expensive regexes or contacting real login services. The application also includes short questions so users can test their understanding.

The main lesson for me is that security risks can come from performance characteristics and observable behavior, not only from incorrect outputs or obvious programming bugs. I also learned that a teaching visualization must be explicit about its assumptions: modeled comparisons, possible regex partitions, and synthetic response times are helpful for intuition, but they are not exact measurements of every real implementation.

Reviewing the timing model also highlights why simulated measurements need realistic assumptions: network delay should not produce negative response times, and the chart should show the samples used in its averages. Before submission, I need to complete my own browser testing and revise this draft to describe my actual experience.
