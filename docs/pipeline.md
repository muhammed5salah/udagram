## Udagram Pipeline

![Pipeline](the-pipeline-overview.png)

### Continuous Integration
#### GitHub
The developers commit and push their code to the GitHub repository which is linked to the CircleCI platform.
GitHub triggers the CircleCI platform when code is pushed to the repository.

#### CircleCI
CircleCI reads the `.circleci/config.yml` file which tells the service what has to be done. In the case of Udagram,
there is a jobs (build) to be run by CircleCI.

- **Backend-api**: Runs the  `backend:install`, `backend:build`, `backend:deploy` script, exports all environment variables from CircleCI configuration and setvalue to app envirnment using eb in `deploy.sh` file, and uses AWS CLI to upload archive to Elastic beanstlk.

- **Frontend-api**: Runs the `frontend:install`, `frontend:build`, `frontend:deploy` script given in the `package.json` file. Then uses AWS CLI to upload assets to S3.
