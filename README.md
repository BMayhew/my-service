# Repository Dispatch Example (Service Source Repo)

The build-deploy.yml file is the job that would get run when the service is updated.

The final step is what calls the test repo and kicks off a `test` github action.

NOTE: you will need to created and add a `REPO_ACCESS_TOKEN` to the github action secrets for this to work.

```bash
      - name: Kick Off Playwright Test Job
        uses: peter-evans/repository-dispatch@v1
        with:
          token: ${{ secrets.REPO_ACCESS_TOKEN }}
          repository: bmayhew/my-tests
          event-type: run-my-tests
          client-payload: '{"github": ${{ toJson(github) }}}'
```
