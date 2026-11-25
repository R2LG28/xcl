# GPU and Runtime Diagnostics

This guide helps contributors collect reproducible evidence when XCL encounters GPU initialization, resource allocation, rendering, or runtime failures. It is diagnostic guidance only; it does not imply that a particular title or configuration is supported.

## Before collecting a report

- Record the XCL revision (commit hash), build type, Windows version, GPU model, driver version, and available system memory.
- Reproduce the issue once with the same launch conditions and preserve the complete log from process start.
- Avoid posting proprietary game files, private account data, access tokens, or unrelated personal information.

## GPU initialization and resource allocation

When an initialization or resource-allocation operation fails:

1. Record the operation name and HRESULT/error code exactly as reported.
2. Distinguish GPU-local memory, shared/system memory, and virtual address-space limits; do not assume they are interchangeable.
3. Capture memory usage before and after the failed operation if the logging interface exposes it.
4. Record whether the failure is repeatable and whether other applications are consuming significant GPU or system memory.
5. Avoid treating a single allocation failure as proof of a driver defect or hardware incompatibility.

## Rendering failures and blank output

A blank or incomplete frame is not, by itself, evidence that the display or GPU is defective. Collect:

- The earliest rendering-related warning or error, not only the final message.
- Counts of submitted, skipped, or failed work, where available.
- Whether the failure occurs during initialization, loading, or steady-state rendering.
- Any diagnostic output from the graphics API or shader compiler.

Do not infer that a later successful operation cancels out an earlier failure.

## Crash reports

For an access violation or other process crash, record:

- Exception type and code.
- Whether the report identifies a read, write, or execute fault.
- Faulting module and offset, if provided.
- The preceding log lines and the steps needed to reproduce.

An address or offset alone does not establish root cause. Avoid attributing a crash to a specific subsystem without supporting evidence.

## Useful report template

- **XCL revision:**
- **Build type:**
- **Windows version:**
- **GPU and driver:**
- **System memory:**
- **Failure stage:**
- **Exact error / HRESULT:**
- **Reproducibility:**
- **Relevant log excerpt:**

A concise, complete report is generally more useful than a speculative fix.
