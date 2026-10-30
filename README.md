# Ajax Mailing

A small PHP contact form that submits without reloading the page. The browser validates the form and sends it with jQuery AJAX to a PHP script, which emails the message using PHP's built-in `mail()` function.

## Features

- Contact form with name, email address, and message fields ([index.php](index.php)).
- Client-side validation: all three fields are required, and the email address is checked against a regular expression. Errors appear in a message area under the form.
- Asynchronous submission via `$.ajax` POST to `ajax.php`, with a loading GIF ([Loader.gif](Loader.gif)) while the request is in progress.
- Server-side handler ([ajax.php](ajax.php)) that sends an HTML email and returns a green success or red failure message. The message is shown after a 2-second delay.

## Tech Stack

- PHP, using the built-in `mail()` function
- jQuery 3.3.1 (bundled in [js/jquery.min.js](js/jquery.min.js))
- Bootstrap 3.3.7 CSS (bundled in [css/bootstrap.min.css](css/bootstrap.min.css))

There is no package manager, build step, or database.

## Getting Started

### Prerequisites

- PHP with a working mail setup (for example a configured sendmail/SMTP relay), since `mail()` depends on the server's mail configuration.

### Configuration

The recipient address is hardcoded in the `$to` variable in [ajax.php](ajax.php). Change it to your own address before using the form.

### Running the Project

Serve the project directory with any PHP-capable web server. For example, using PHP's built-in server:

```bash
php -S localhost:8000
```

Then open `http://localhost:8000/index.php`. This command has not been run as part of writing this README, and email delivery depends on your local mail configuration.

## Usage

1. Open `index.php` in the browser.
2. Fill in the name, email address, and message fields.
3. Click **Submit**. If a field is empty or the email address is invalid, an error message appears below the form.
4. Otherwise a loading indicator is shown, then a success or failure message from `ajax.php`.

## Project Structure

```text
.
├── index.php               # Form page and client-side jQuery logic
├── ajax.php                # Receives the POST request and sends the email
├── Loader.gif              # Loading indicator
├── css/bootstrap.min.css
└── js/jquery.min.js
```
