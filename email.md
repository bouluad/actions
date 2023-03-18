This composite action uses the curl command-line tool to send an email via SMTP. It requires several inputs, including the SMTP server address and port, the email account username and password, the recipient email address, the email subject, and the email body.

The action uses the actions/checkout action to check out the repository code, and then uses curl to send the email. The --url option specifies the SMTP server address and port, while the --mail-from and --mail-rcpt options specify the sender and recipient email addresses. The --user option provides the email account credentials, while the --header option sets the email subject line. Finally, the --data option sets the email message body.

To use this action, you can create a workflow that triggers on a push to the main branch, and provides the required inputs as workflow variables. For example:

'''
name: Send email on push

on:
  push:
    branches: [ main ]

jobs:
  send_email:
    runs-on: ubuntu-latest

    steps:
      - name: Send email
        uses: my-org/send-email-action@v1
        with:
          smtp_server: smtp.gmail.com
          smtp_port: 587
          username: ${{ secrets.EMAIL_USERNAME }}
          password: ${{ secrets.EMAIL_PASSWORD }}
          to_email: recipient@example.com
          subject: New push to main branch
          body: A new push has been made to the main branch.
'''
This workflow triggers the send_email job on every push to the main branch, and provides the required inputs using workflow variables. The secrets.EMAIL_USERNAME and secrets.EMAIL_PASSWORD variables are assumed to be set in the repository secrets.
