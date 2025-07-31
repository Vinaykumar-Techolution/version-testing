Automated Semantic Versioning and Deployment to GKE
This project demonstrates two powerful CI/CD pipelines for automatically building, versioning, and deploying a containerized application to Google Kubernetes Engine (GKE). Both pipelines implement semantic versioning based on commit messages, ensuring a consistent and automated release process.

The core logic involves:

Storing the current version number in a version.txt file in a Google Cloud Storage (GCS) bucket.

Reading the latest commit message to determine the type of version bump (major, minor, or patch).

Building and tagging a new Docker image with the bumped version.

Pushing the image to Google Artifact Registry.

Deploying the new image to a GKE cluster.

Updating the version.txt file in GCS upon a successful deployment.

Versioning Strategy: Conventional Commits
Both pipelines follow the Conventional Commits specification to automate semantic versioning. The pipeline analyzes the latest commit message for specific keywords to determine the version bump:

Major Bump (e.g., 1.x.x → 2.0.0): Triggered if the commit message body or footer contains BREAKING CHANGE:.

Example: feat: drop support for v1 API\n\nBREAKING CHANGE: endpoint removed

Minor Bump (e.g., 1.0.x → 1.1.0): Triggered if the commit message starts with feat:.

Example: feat: add OTP login support

Patch Bump (e.g., 1.0.0 → 1.0.1): Triggered if the commit message starts with fix:, or if no other keyword is found (default).

Example: fix: handle null in login API
