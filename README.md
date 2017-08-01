Before running `rake db:seed` make sure you get your Country, State and County models as follows :
```
create_table :countries do |t|
	t.string :name
	t.string :iso
  t.timestamps
end
```
```
create_table :states do |t|
	t.references :country
	t.string :name
	t.string :iso
  t.timestamps
end
```
```
create_table :counties do |t|
	t.references :state
	t.string :name
	t.integer :zip_code
  t.timestamps
end
```
run `rake db:migrate` and then `rake db:seed`
and make sure you set up the relations between the models as follows:
Country has_many :states
State belongs_to :country
State has_many :counties
County belongs_to :state
