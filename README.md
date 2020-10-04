# Basecamp API v3 Integration
This is a Drupal module that facilitates using the [https://github.com/basecamp/bc3-api](Basecamp API v3). 

As an integration module, this facilitates transactions between the Basecamp endpoints, and requires simple coding to achieve this.

After creating an authorized application & storing the initial access token & refresh token, this module will continue to renew the token
via a cron job that runs once per day.

Once complete, actions, such as creating a new todo, are as simple as:

```php
$data = [
  'content' => $title,
  'description' => $message,
  'due_on' => date('Y-m-d', strtotime('+7 days')),
  'notify' => TRUE,
  'assignee_ids' => [1,2,3],
];
$project = $config->get('project');
$list = $config->get('list');
  
Basecamp::createTodo($project, $list, $data);
```
