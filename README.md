# laminas-mail

[![Build Status](https://travis-ci.com/laminas/laminas-mail.svg?branch=master)](https://travis-ci.com/laminas/laminas-mail)
[![Coverage Status](https://coveralls.io/repos/github/laminas/laminas-mail/badge.svg?branch=master)](https://coveralls.io/github/laminas/laminas-mail?branch=master)
Oauth2 Support of the `Laminas\Mail`

`Laminas\Mail` provides generalized functionality to compose and send both text and
MIME-compliant multipart email messages. Mail can be sent with `Laminas\Mail` via
the `Mail\Transport\Sendmail`, `Mail\Transport\Smtp` or the `Mail\Transport\File`
transport. Of course, you can also implement your own transport by implementing
the `Mail\Transport\TransportInterface`.

- File issues at https://github.com/laminas/laminas-mail/issues
- Documentation is at https://docs.laminas.dev/laminas-mail/

```
use Laminas\Mail\Storage\Imap;
use Laminas\Mail\Protocol\ImapOauth;
use Laminas\Mail\Protocol\Imap as Laminas_Mail_Protocol_Imap;
use Laminas\Mail\Storage;

//Sample
// Connecting with Imap:
if($auth == 'token'){ //if auth is Oauth use ImapOauth interface
  $imapProtocol = new ImapOauth("imap.gmail.com", 901, "SSL");  
  $imap =   $imapProtocol->loginOauth('user', $accessToken);
  if($imap){
    $mail = new Imap($imapProtocol);
  }
} else {
  //use normal lamina 
  $mail = new Imap(['host'=>'imap.gmail.com','user'=>'user','password'=>'password']);
}


if($mail){
  $mail->selectFolder("INBOX");
}
```
