# Repository Dispatch Example (Service Source Repo)

The build-deploy.yml file is the job that would get run when the service is updated.

The final step is what calls the test repo and kicks off a `test` github action.

Dispatch an event to a remote repository using a `repo` scoped [Personal Access Token (PAT)](https://docs.github.com/en/authentication/keeping-your-account-and-data-secure/creating-a-personal-access-token).

```yml
      - name: Kick Off Playwright Test Job
        uses: peter-evans/repository-dispatch@v2
        with:
          token: ${{ secrets.REPO_ACCESS_TOKEN }}
          repository: bmayhew/my-tests
          event-type: run-my-tests
          client-payload: '{"github": ${{ toJson(github) }}}'
```
