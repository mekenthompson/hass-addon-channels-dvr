# Agent Instructions

## Development & Release Workflow

When modifying the Channels DVR add-on, follow these steps to ensure proper release management:

1.  **Update Version**:
    - Increment the `version` key in `channels-dvr/config.yaml`.
    - Use Semantic Versioning (Patch `x.x.Y` for bug fixes, Minor `x.Y.x` for features).

2.  **Update Changelog**:
    - Add a new section at the top of `channels-dvr/CHANGELOG.md`.
    - Format:
        ```markdown
        ## 1.0.X

        - Description of changes
        ```

## Repository Structure
- **Add-on Source**: `channels-dvr/`
- **Configuration**: `channels-dvr/config.yaml` (Metadata, Options, Ports)
- **Build**: `channels-dvr/Dockerfile` (Generates run script dynamically)
- **Documentation**: `channels-dvr/DOCS.md`
