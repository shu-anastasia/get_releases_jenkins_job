@Library('test_task_lib') _
import com.as.GetGitHubReleases

def repo_url = params.repo_url

properties(
    [
        parameters(
            [   string(name: 'repo_url', defaultValue: '',
                    description: 'GitHub repository to get releases from')
            ]
        )
    ]
)

node {
    stage('Get Releases') {
        retry(3){
            timeout(time: 10, unit: 'SECONDS'){
                def getGitHubReleases = new GetGitHubReleases(this)
                getGitHubReleases.getReleases(repo_url)
            }
        }
    }
}