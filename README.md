# Clojure-mail


```
[clojure-mail "0.1.0-SNAPSHOT"]
```

A clojure library mainly aimed at parsing, downloading and reading email from Gmail servers.

Possible uses for this library include machine learning corpus generation and command line mail clients.

There are currently some issues with handling large volumes of mail (i.e hundreds or thousands of messages)

## Examples

In this example we'll log into a Gmail account and read messages from the inbox and spam folders.

The first thing we need to do is create a mail store that acts as a gateway to your gmail account.

```clojure
(def store (gen-store "USER@GMAIL.COM" "PASSWORD"))
```

Now we can get 5 messages from our inbox

```clojure
(def my-messages (take 5 (get-inbox)))
```

And read the first message in our inbox

```clojure
(msg/read-message (first (get-inbox)))
```

Or read a message from the spam folder

```clojure
(def spam (take 5 (get-spam)))
```

## Message parsing

Get all headers from an email

```clojure

;; Get an email message from our inbox

(def m (first (get-inbox)))

;; Returns all headers as a map

(msg/message-headers m)

;; Get the sender

(msg/sender m)

;; Get the from address

(msg/from m)

```

## Listing Mail Folders

You can return a list of mail folders easily

```clojure
(folders store)

;; (("INBOX") ("Important Info") ("Zero" ("Group") ("Newsletter")
;;  ("Notification") ("Registration")) ("[Gmail]" ("All Mail")
;;  ("Drafts") ("Important") ("Sent Mail") ("Spam") ("Starred")
;;  ("Trash")) ("[Mailbox]" ("Later") ("To Buy") ("To Read") ("To Watch")))
```

## Unread messages

Fetch unread emails

```clojure

(unread-messages "INBOX")

```

## License

Copyright © 2012 FIXME

Distributed under the Eclipse Public License, the same as Clojure.
