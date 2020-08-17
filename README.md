# Assorted Snippits

**Hack any paid WiFi hotspot in about 30 seconds**
```
ifconfig en1 | grep ether
arp -a
sudo ifconfig en1 ether [mac address to spoof]
```

# Git Command

* `git init` creates a new Git repository
* `git status` inspects the contents of the working directory and staging area
* `git add` adds files from the working directory to the staging area
* `git diff` shows the difference between the working directory and the staging area
* `git commit` permanently stores file changes from the staging area in the repository
* `git log` shows a list of all previous commits
* `git reset --hard` Revert changes to modified files.
* `git clean -fd` Remove all untracked files and directories.
* `git checkout -b topic-branch` # To create New Branch
* `git branch` # To check branch which you are in
* `git checkout master` # To return to master branch or change another branch

# Create Multiple Skype in Mac

* Open Terminal
* type this in terminal ```$ sudo /Applications/Skype.app/Contents/MacOS/Skype /secondary```

# Compress image on wordpress via functions

* Open function.php
* add this code ```add_filter( 'jpeg_quality', create_function( '', 'return 80;' ) );```

# Here are all the Rails 4 (ActiveRecord migration) datatypes:
```
  :binary
  :boolean
  :date
  :datetime
  :decimal
  :float
  :integer
  :primary_key
  :references
  :string
  :text
  :time
  :timestamp
```

# Here are all the Rails 5 (ActiveRecord migration) datatypes:
```
	:primary_key
	:string
	:text
	:integer
	:bigint
	:float
	:decimal
	:numeric
	:datetime
	:time
	:date
	:binary
	:boolean
```

# Date and time Format meaning

* `%a` - The abbreviated weekday name (“Sun”)
* `%A` - The full weekday name (“Sunday”)
* `%b` - The abbreviated month name (“Jan”)
* `%B` - The full month name (“January”)
* `%c` - The preferred local date and time representation
* `%d` - Day of the month (01..31)
* `%H` - Hour of the day, 24-hour clock (00..23)
* `%I` - Hour of the day, 12-hour clock (01..12)
* `%j` - Day of the year (001..366)
* `%m` - Month of the year (01..12)
* `%M` - Minute of the hour (00..59)
* `%p` - Meridian indicator (“AM” or “PM”)
* `%S` - Second of the minute (00..60)
* `%U` - Week number of the current year, starting with the first Sunday as the first day of the first week (00..53)
* `%W` - Week number of the current year, starting with the first Monday as the firstday of the first week (00..53)
* `%w` - Day of the week (Sunday is 0, 0..6)
* `%x` - Preferred representation for the date alone, no time
* `%X` - Preferred representation for the time alone, no date
* `%y` - Year without a century (00..99)
* `%Y` - Year with century
* `%Z` - Time zone name
* `%%` - Literal “%” character
* `%e` - Day of the month, without leading zero (1..31)
* `%-I %-d` - You can remove leading Zeros this way as well. By just adding a - symbol.

# Outpting any files using only terminal 

eg: JSON to CSV

`curl -u 60783dd23ef:X https://your-domain.com/v1/filename.json -O`
or 
`curl -u 60783dd23ef:X https://your-domain.com/v1/filename.json -o mailbox.csv`

# downloading lots of files via terminal
`for((i=1;i<=8;i++)); do curl -u xxxxxx:pass //your-domain.com/v1/filename.json?page=$i -o mailboxes-28303-conversations-page-$i.json; done`

# FQL facebook search by group name

```sql
SELECT gid, name, privacy, website, email
FROM   group
WHERE  CONTAINS("jobs")
AND    strpos(lower(name),lower("jobs")) >=0
```

# Facebook FQL Operator

```
me()
now()
rand()
strlen(...)
concat(...)
substr(...)
strpos(...)
lower(...)
upper(...)
contains(...)
order by
SELECT, WHERE
AND, OR, NOT, IN, ><=, +-*/  
```
# Ruby Sample Scraper

```ruby
require 'open-uri'
require 'nokogiri'

url = 'https://en.wikipedia.org/wiki/List_of_current_NBA_team_rosters'
page = Nokogiri::HTML(open(url))

# page.css('a') to get all a tags
# page.css('li.toclelev-3') to get content within li

page.css('td[style="text-align:left;"]').each do |line|
	puts line.text
end
```

# Rails tips
this will be run in termminal window

# Checking rake task
`rake db -T -A`

# create a new rake task 
`rails generate task scraper scrape  destroy_all_posts`

# where **scraper** is the name of the rake **scrape**  and **destroy_all_posts** are the name of the task being rake.

# Rake Command
```ruby
rake db:create          # Create the database from DATABASE_URL or config/database.yml for the current Rails.env (use db:create:all to create all dbs in the config)
rake db:drop            # Drops the database using DATABASE_URL or the current Rails.env (use db:drop:all to drop all databases)
rake db:fixtures:load   # Load fixtures into the current environment's database
rake db:migrate         # Migrate the database (options: VERSION=x, VERBOSE=false)
rake db:migrate:status  # Display status of migrations
rake db:rollback        # Rolls the schema back to the previous version (specify steps w/ STEP=n)
rake db:schema:dump     # Create a db/schema.rb file that can be portably used against any DB supported by AR
rake db:schema:load     # Load a schema.rb file into the database
rake db:seed            # Load the seed data from db/seeds.rb
rake db:setup           # Create the database, load the schema, and initialize with the seed data (use db:reset to also drop the db first)
rake db:structure:dump  # Dump the database structure to db/structure.sql
rake db:version         # Retrieves the current schema version number
```

# Migrations Tips

**Remove Column**

`rails g migration RemoveColumnFromDatabaseTable 'first_name:string'`

**Rename Column**

Create a Migration

`rails g migration RenameNameToFirstNameInOrders`

after that go to `db/migrate/20160521114448_rename_name_to_first_name_in_orders.rb`

and add this

```ruby
class RenameNameToFirstNameInOrders < ActiveRecord::Migration

  def change
    rename_column :orders, :name, :first_name
  end

end
```

then 
`rake db:migrate`

# Rake Db Reference 3.2 +


* `db:create` creates the database for the current env
* `db:create:all` creates the databases for all envs
* `db:drop drops` the database for the current env
* `db:drop:all` drops the databases for all envs
* `db:migrate` runs migrations for the current env that have not run yet
* `db:migrate:up` runs one specific migration
* `db:migrate:down` rolls back one specific migration
* `db:migrate:status` shows current migration status
* `db:rollback` rolls back the last migration
* `db:forward` advances the current schema version to the next one
* `db:seed` (only) runs the db/seed.rb file
* `db:schema:load` loads the schema into the current env's database
* `db:schema:dump` dumps the current env's schema (and seems to create the db as well)
* `db:setup` runs db:schema:load, db:seed
* `db:reset` runs db:drop db:setup
* `db:migrate:redo` runs (db:migrate:down db:migrate:up) or (db:rollback db:migrate) depending on the specified migration
* `db:migrate:reset` runs db:drop db:create db:migrate


# Update Database table using seed.rb

```ruby
my_account_1 = Account.find_or_initialize_by(operator_id: "1")

my_account_1.update(
			operator_logo: '', 
			operator_name: 'Ruel Nopal', 
			business_name: 'RNopal Ltd.', 
			bus_name: 'Super Line', 
			business_address: 'Pasig City', 
			operator_id: '1',
			telephone: '7654321', 
			mobile: '0987654321')
```
# Uploading files from local computer to remote location
```
scp your-files.zip root@xxx.x.xxx.xxx:/your/destination/folder
```
# How to Change the number of icons in launchpad or Application

By default there are 7×5 icons (35 icons in total). You can change this to anything you want with a couple of simple commands in the terminal.


To show 100 icons (10×10), open terminal and type
```
defaults write com.apple.dock springboard-rows -int 10
defaults write com.apple.dock springboard-columns -int 10
```
To show 50 icons (5×10), open terminal and type
```
defaults write com.apple.dock springboard-rows -int 10
defaults write com.apple.dock springboard-columns -int 5
```
# How to see files in linux command

a] `ls command` – list directory contents.

b] `du command` – estimate file space usage.

c] `stat command` – display file or file system status.

To determine the size of a file called /bin/grep, enter:

To Determine all storage size
```
df -h
```
output
```
Filesystem      Size  Used Avail Use% Mounted on
/dev/vda1        59G   44G   13G  77% /
devtmpfs        3.9G     0  3.9G   0% /dev
tmpfs           3.9G     0  3.9G   0% /dev/shm
tmpfs           3.9G  401M  3.5G  11% /run
tmpfs           3.9G     0  3.9G   0% /sys/fs/cgroup
/dev/sda         99G   30G   64G  32% /home1
/dev/loop0      1.9G  3.2M  1.8G   1% /tmp
tmpfs           783M     0  783M   0% /run/user/0
```

Determine Current Folder size

```
du -sh *
du -hs * | sort -h
```

output
```
4.0K	backup
0	bin
229M	boot
44K	cldeploy
0	dev
43M	etc
0	lib
0	lib64
16K	lost+found
4.0K	media
4.0K	mnt
289M	opt
0	proc
4.0K	razor-agent.log
9.3M	root
73M	run
0	sbin
0	scripts
4.0K	srv
0	sys
128K	tmp
11G	usr
c2.5G	var
```

```
ls -l /bin/grep
```
output
```
-rwxr-xr-x 1 root root 175488 May 13  2012 /bin/grep
```
In the above output example, the `175488` is the size of the file. For a more user friendly output, pass the -h option to the ls command:

```
ls -lh /bin/grep
```
output
```
-rwxr-xr-x 1 root root 172K May 13  2012 /bin/grep
```

In the above output example, the 172K is the size of the file. The `du command` provides the same output in a more user friendly way and it hides all other details too:

```
du -h /bin/grep
```
output

```
172K	/bin/grep
```
Finally, `stat command` also provide file size:

```
stat /bin/grep
```

output

```
stat /bin/grep
  File: `/bin/grep'
  Size: 175488    	Blocks: 344        IO Block: 4096   regular file
Device: 900h/2304d	Inode: 5505033     Links: 1
Access: (0755/-rwxr-xr-x)  Uid: (    0/    root)   Gid: (    0/    root)
Access: 2013-06-10 01:31:37.520022359 +0530
Modify: 2012-05-13 18:17:28.000000000 +0530
Change: 2013-05-17 02:16:17.138033825 +0530
```
source: http://www.cyberciti.biz/faq/how-to-see-file-size-on-linux-unix/

# How to limit page view wordpress
```php
// Exit if accessed directly
if ( !defined( 'ABSPATH' ) ) {
	exit;
}
```
# How to Force Backup WHM
```
/usr/local/cpanel/bin/backup --force
```
to monitor
```
tail -f /usr/local/cpanel/logs/cpbackup/{id}.logs
```
# How to add php code inside terminal

**make sure php-cli is install**

```
$ echo "<?php phpinfo(); ?>" >> info.php
```
# Find a string inside files ain all folders and its sub folder and list it in terminal
good for finding malware
```
grep -lr 'kdzooma' * >> list.txt
```
# Remove __MACOSX/ in folder when zipping
```
zip -d your-archive.zip "__MACOSX*"
```
# How to flush Cache in Mac using terminal
```
$ sudo dscacheutil -flushcache;sudo killall -HUP mDNSResponder; say cache flushed
```
# Find files in terminal
```
$ find . -type f -name "dns"
```
Find folder in terminal
```
$ find / -name "dns"
```
# list of all DNS record in WHM/cpanel
```
$ cd /var/named
```
# How to to dump sql in terminal
```

#Dumping single db table
$ mysqldump --single-transaction -u db_user -p db_name db_table_name > sqldump.sql

#Dumping single database
$ mysqldump --single-transaction -u db_user -p db_name > sqldump.sql
```
# How to Uploald sql in terminal
```
$ mysql -u username -p database_name < file.sql
```
# Hide Desktop Icon for Mac

```
$ defaults write com.apple.finder CreateDesktop -bool false;killall Finder
```
# Show Desktop Icon For Mac 

```
Type in defaults write com.apple.finder CreateDesktop -bool true;killall Finder
```
# Clean All Users Trash
```
find /home*/*/.trash/* -exec rm -rf {} \;
```

# Upload image in Wordpress frontend using Advance Custom field (ACF)
```php
if ( ! function_exists( 'wp_handle_upload' ) ) {
    require_once( ABSPATH . 'wp-admin/includes/file.php' );
}

//Upload company logo
$upload_overrides = array( 'test_form' => false );
// From File field
$organizer_img_upload = $_FILES['organizer_img_upload'];
$organizer_img_file_return = wp_handle_upload( $organizer_img_upload, $upload_overrides );



//file upload and get image id
if ($organizer_img_file_return) {
	$wp_upload_dir = wp_upload_dir();
	$attachment = array(
	'guid' => $wp_upload_dir['url'].'/'.basename($organizer_img_file_return['file']),
	'post_mime_type' => $organizer_img_file_return['type'],
	'post_title' => preg_replace('/\.[^.]+$/', '', basename($organizer_img_file_return['file'])),
	'post_content' => '',
	'post_status' => 'inherit'
	);
	$attach_id = wp_insert_attachment($attachment, $organizer_img_file_return['file']);

	// Make sure that this file is included, as wp_generate_attachment_metadata() depends on it.
	require_once( ABSPATH . 'wp-admin/includes/image.php' );

	// Generate the metadata for the attachment, and update the database record.
	$attach_data = wp_generate_attachment_metadata( $attach_id, $organizer_img_file_return['file'] );
	wp_update_attachment_metadata( $attach_id, $attach_data );

	
	// Add ACF image field
	update_field('company_logo', $attach_id, $post_id);
}
```
# How to solve inner page 404 error ubunto
1. go to `cd /etc/apache2/sites-available` find your virtualhost
2. make sure this  code is present
```
	<Directory /var/www/yourdomain.com/public_html>
            Options Indexes FollowSymLinks
            AllowOverride All
            Require all granted
        </Directory>
```
# Create ssh-keygen with pem
```
ssh-keygen -m PEM -t rsa
```
# Run Nodejs continuesly
```
$ node index.js && nohup -& (to run as a background process - no hiccup)
```
