# ICS Mini-project

The ICS project is broken into 3 subparts: sql-injection, XSS, and XSS secure

## sql-injection

This demonstrates a sql-injection attack.

1. navigate to /sql_injection
2. run $ python3 manage.py runserver
3. go [link here](127.0.0.1:8000/items/search)
4. type this in search query: ' UNION SELECT first_name FROM auth_user WHERE first_name LIKE ' (with quotes)

## XSS

This is a todo app for group projects, where only admin can delete all tasks. It demonstrates how an XSS attac can delete all tasks when the admin logs in.

1. navigate to /todo
2. run $ python3 manage.py runserver
3. go [link here](127.0.0.1:8000/all)
4. add a few tasks
5. add the following task:
        <pre><code>Malicious Code<form id="myform" action="http://127.0.0.1:8000/deleteall" method="post"></form>
        <script type="text/javascript">
            setTimeout(() => {document.getElementById("myform").submit();}, 5000);
        </script></code></pre>
6. go [link here](127.0.0.1:8000/admin) and log in with user=admin pass=0348
7. visit [link this](127.0.0.1:8000/all) after login, and wait for 5 seconds, all tasks will be deleted automatically

## XSS secure

This is secure version of the same todo app. Follow the same steps as above, the attack doesn't work on this.
