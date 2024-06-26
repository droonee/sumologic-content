# Sumo Logic for RDS Enhanced Monitoring
Sumo Logic Community Content built for RDS Enhanced Monitoring not yet published to the [App Catalog](https://help.sumologic.com/docs/integrations/).

AWS offers monitoring of RDS instances out of the box through CloudWatch Metrics. They also offer a more in-depth monitoring at the OS-level through the use of [Enhanced Monitoring](https://docs.aws.amazon.com/AmazonRDS/latest/UserGuide/USER_Monitoring.OS.html). Enhanced Monitoring sends performance logs to CloudWatch Logs. While Sumo Logic can ingest these performance logs through the use of the standard [CloudWatch Logs Lambda function](https://help.sumologic.com/docs/send-data/collect-from-other-data-sources/amazon-cloudwatch-logs/collect-with-lambda-function/), ingesting them as a timeseries metric will provide more real-time analysis at a fraction of the cost.

![RDS Enhanced Monitoring - Overview dashboard](https://raw.githubusercontent.com/SumoLogic/sumologic-content/master/Amazon_Web_Services/RDS/Enhanced-Monitoring/Screenshots/RDS-Enhanced-Monitoring-Overview.png)

**Note: This current version does not support Microsoft SQL Server yet. See [AWS documentation](https://docs.aws.amazon.com/AmazonRDS/latest/UserGuide/USER_Monitoring.OS.html) for supported metrics for other engines.**

### To use the content:
- Download the JSON file(s).
- Find/replace all Source Categories within the JSON with your own Source Category (Ex: sourceCategory=yourSourceCategory).
- [Import](https://help.sumologic.com/docs/get-started/library/#import-content) the content to your desired folder location in Sumo Logic.

### Collection:
To ingest the Enhanced Monitoring logs, a modified version of the Lambda function was made to convert them into Carbon 2.0 metric format before sending to Sumo Logic.

Setup of the Lambda function follows [Collecting Amazon CloudWatch Logs using a Lambda Function](https://help.sumologic.com/docs/send-data/collect-from-other-data-sources/amazon-cloudwatch-logs/collect-with-lambda-function/). Subscribe the function created from rds_enhanced_lambda.js to the CloudWatch log group created for the Enhanced Monitoring logs (typically RDSOSMetrics).

### To upload your own content:
Please see [Sumo Logic Community Ecosystem Apps FAQs](https://help.sumologic.com/docs/integrations/community-ecosystem-apps/#faq).

### To add review/comment to content:
Please provide a review/comment for this content by following the guidelines below:

- Select the **Comments** folder.
- Open the **Comments.json** file.
- Select Edit (pen icon).
- Add a new line below the current comments, and paste in your review/comment using the following schema:

        {
            "reviewer":"[githubid/name]",
            "ratings":{
                "overall":4,
                "use-case":5,
                "design":4,
                "technical":4
            },
            "review":"This app is very useful for knowing x, y, and z. It would be great if the dashboards were broken out by use case instead of being one big dashboard."
        }


- Select **Propose New Changes**.
- Submit **Pull Request**.

Code owners will review and merge your comments on the content to the repo.

Please see [How to add a review/comment to an app](https://help.sumologic.com/docs/integrations/community-ecosystem-apps/#how-do-i-add-a-reviewrating-to-an-app) for more information.