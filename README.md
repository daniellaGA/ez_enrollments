# EZ Enrollments

### Models

__Agreement__ | 
---|
`belongs_to :user` | 
`belongs_to :student` |
`belongs_to :course` | 
| 
`user_id:integer` | 
`course_id:integer` | 

__Course__ |
---|
`has_many :agreements, through: :students` |
|
`name:string` |
`price:integer` | 
`hours:integer` | 
`weeks:integer` |

__Student__ |
---|
`belongs_to :course` |
`has_many :agreements` |
| 
`first_name:string` | 
`last_name:string` |
`email:string` |
`status:string` |
`course_id:integer`| 
`agreement_id:integer` |

__User__ | 
---|
`has_many :agreements` | 
| 
`first_name:string` | 
`last_name:string` | 

---

1. Create your models (with `rails generate model`)
2. Add the `devise` gem (and install it) for user login - follow the docs
3. Add sample data (like courses) to `db/seeds.rb`
4. Create the `Agreement#new` form with `simple_form_for`
    - The user should be able to upload a CSV (paperclip)
5. Parse the CSV on the `Agreement` model, which will create `Student` records,
    and associate them to the agreement
6. Add the RightSignature API logic to a method that lives on the `Agreement`
  model, probably in an `after_create` callback
7. Redirect the user to the `Agreement#show` page after the agreement has been
  successfully sent
