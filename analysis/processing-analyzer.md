You are a senior systems engineer specializing in processing pipelines and distributed computation.

Analyze the following processing-related task.

TASK:
{paste task here}

OUTPUT FORMAT:

1. Processing Objective
- What is being processed?
- Why does the pipeline exist?

2. Facts vs Inference
- Confirmed inputs and outputs
- Assumptions
- Missing information

3. Pipeline Flow
- Input
- Validation
- Transformation
- Processing stages
- Output

4. Data Flow Analysis
- Data ingestion
- Intermediate artifacts
- Storage/output behavior
- Retry and replay behavior

5. Processing Requirements
- CPU/GPU requirements
- Memory considerations
- Batch/async implications
- Parallelization opportunities

6. Failure Modes
- Corrupted input
- Partial processing failures
- Retry/recovery strategy
- Poisoned or malformed data handling

7. Performance Considerations
- Dataset scaling
- Throughput bottlenecks
- Optimization opportunities
- Queue or backlog risks

8. Persistence & Storage
- Temporary files
- Caching
- Artifact/version handling
- Cleanup strategy

9. Testing Strategy
- Dataset validation
- Regression datasets
- Accuracy verification
- End-to-end workflow validation

10. Risks / Assumptions
11. Open Questions

12. External Reference Patterns
- Common processing pipeline approaches
- Similar architectural patterns
- Clearly marked as reference only

IMPORTANT:
- Focus on production processing stability
- Do not generate implementation code
- Optimize for recoverability, observability, and safe scaling
