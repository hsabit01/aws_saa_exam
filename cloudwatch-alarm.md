# CloudWatch Alarm

## Simple Explanation
CloudWatch Alarm watches a CloudWatch metric and checks whether it crosses a limit you set.  
When that happens, it changes state and can trigger an action like sending a notification or scaling resources.

## Key Use Case
- Alert when CPU, memory, or errors go too high 🚨
- Trigger Auto Scaling when workload increases 📈

## Practical Scenario
Your EC2 web server gets busy during office hours.  
You create a CloudWatch Alarm for high CPU usage.  
If CPU stays above 80%, the alarm sends an SNS notification or scales out more instances.

## Exam Tip
- Think: metric threshold + action.
- Alarm watches metrics, not application logs directly.

## Difference Comparison

| Service | Best For | Key Difference |
|---------|----------|----------------|
| CloudWatch Alarm | Threshold alerts | Reacts to metric state changes |
| EventBridge | Event routing | Reacts to events, not metric thresholds |

## Muscle Memory One-Liner
**CloudWatch Alarm = “If metric crosses the line, do something.”**

## Visual Diagram

```mermaid
flowchart LR
    A([ 📊 CloudWatch Metric ])
    B{ 🚨 Threshold? }
    C([ 🔔 SNS Alert ])
    D([ 📈 Auto Scaling ])

    A --> B
    B -- Yes --> C
    B -- Yes --> D
    B -- No --> E([ ✅ OK State ])

    style A fill:#1d4ed8,color:#ffffff,stroke:#0f172a,stroke-width:2px
    style B fill:#f59e0b,color:#111827,stroke:#0f172a,stroke-width:2px
    style C fill:#dc2626,color:#ffffff,stroke:#0f172a,stroke-width:2px
    style D fill:#16a34a,color:#ffffff,stroke:#0f172a,stroke-width:2px
    style E fill:#7c3aed,color:#ffffff,stroke:#0f172a,stroke-width:2px
```

## Final Summary Table

| Topic | What It Is | Best Use Case | Common Confusion | Memory Hook |
|------|-------------|---------------|------------------|-------------|
| CloudWatch Alarm | Metric-based alert tool | Alert or act on thresholds | EventBridge | If metric crosses the line, act |
