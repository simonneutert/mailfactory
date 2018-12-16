# mailfactory
Create MIME email messages with multiple body parts and attachments in Ruby

## Example

``` ruby
require 'net/smtp'
require 'rubygems'
require 'mailfactory'

# handles headers
mail = MailFactory.new()
mail.to = "test@test.com"
mail.from = "sender@sender.com"

# handles content
mail.subject = "Here are some files for you!"
mail.text = "This is what people with plain text mail readers will see"
mail.html = "A little something <b>special</b> for people with HTML readers"

# handles attachments
mail.attach("/etc/fstab")
mail.attach("/some/other/file")

# does the job
Net::SMTP.start('smtp1.testmailer.com', 25, 'mail.from.domain', fromaddress, password, :cram_md5) do |smtp|
  mail.to = toaddress
  smtp.send_message(mail.to_s(), fromaddress, toaddress)
end
```
