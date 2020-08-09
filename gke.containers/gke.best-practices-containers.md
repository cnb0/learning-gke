# Best Practices for Operating Containers
```


- Use the native logging mechanisms of containers
    - JSON logs
    - Log aggregator sidecar pattern

- Ensure that your containers are stateless and immutable
    - Statelessness
    - Immutability

- Avoid privileged containers
- Make your application easy to monitor
    - Metrics HTTP endpoint
    - Sidecar pattern for monitoring
- Expose the health of your application
    - Liveness probe
    - Readiness probe
- Avoid running as root
- Carefully choose the image version
