Automated Email Sender Using Google Apps Script

🚀 Introduction

This repository contains a Google Apps Script designed to automate daily repetitive email tasks. The script is capable of sending personalized emails to a list of recipients with a pre-defined format, making it a powerful tool for automating daily email notifications, reminders, or any other repetitive email communications.

📌 Features

Sends automated emails on a scheduled basis (daily, except Sundays).

Customizable subject line and email body.

Supports HTML formatting in the email body.

Sends emails to multiple recipients with specified CC and BCC options.

Customizable email table format for better presentation.

📂 File Structure

AutomatedEmailSender.gs: The main script file containing the email automation logic.

README.md: This file, explaining the project.

🚀 How It Works

The script is designed to automatically send emails daily (except Sundays).

The email content is customizable, including the subject and body.

A formatted HTML table is included in the email body, making it visually organized.

The list of recipients is predefined within the script (To, CC, BCC).

🚀 How to Use

Open your Google Drive and create a new Google Apps Script file.

Copy and paste the code from the AutomatedEmailSender.gs file into the script editor.

Set up the time-based trigger to run the script automatically daily.

Customize the subject, body, and recipient list as per your requirements.

Save and authorize the script.

📌 Future Plans

Add support for personalized attachments.

Create a version for sending follow-up emails in bulk with one click.

Make the recipient list dynamic using Google Sheets.


    <<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<SCRIPT>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>

// This script is used to automate a daily reminder email for compliance purposes.

function sendDailyComplianceReminder() {
  const today = new Date();
  const day = today.getDay(); // Sunday = 0, Monday = 1 ... Saturday = 6
  if (day === 0) return; // Skip Sunday

  const formattedDate = Utilities.formatDate(today, Session.getTimeZone(), "d MMM yyyy");

  const subject = "Reminder: Compliance Information Required - " + formattedDate;

  const body = `
Dear Team,<br><br>

This is a gentle reminder to share the necessary compliance information for today.<br>
Please ensure all required details are provided in the specified format to maintain compliance standards.<br><br>

<b>Note: Please follow the format provided below.</b><br><br>

<table border='1' style='border-collapse: collapse; font-family: Calibri, sans-serif; font-size: 11pt;'>
  <tr>
    <th>Name</th>
    <th>Email ID</th>
    <th>Employee ID</th>
    <th>Mobile No.</th>
    <th>Responsible Person</th>
    <th>Department</th>
    <th>Last Working Date</th>
  </tr>
  <tr>
    <td>&nbsp;</td>
    <td>&nbsp;</td>
    <td>&nbsp;</td>
    <td>&nbsp;</td>
    <td>&nbsp;</td>
    <td>&nbsp;</td>
    <td>&nbsp;</td>
  </tr>
</table><br><br>

Best Regards,<br>
Automated Compliance System
`;

  GmailApp.sendEmail(
    "abhishekpsingh64@gmail.com", //To
    subject,
    "",
    {
      htmlBody: body,
      cc: "abhishekpsingh064@gmail.com",
      bcc: "familyconnectacount@gmail.com"
    }
  );
}
