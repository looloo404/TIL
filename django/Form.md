# Form

## Form

- Form에는 일반적으로 사용하는 일반 폼(FORM)이 있고, 모델 폼(model Form)이 있다.
- ModelForm: 모델과 필드를 지정해주면  ModelForm이 Form 필드를 생성해준다.

### Normal Form
```python
#forms.py
from django import forms

#일반 폼(Form)
class BlogForm(forms.Form):
    name = forms.CharField()
    email = forms.EmailField()
    comment = forms.CharField(widget=forms.Textarea)
```

### Model Form example code
```python
#forms.py
from django import forms
from .models import Blog

#모델 폼(ModelForm)
class BlogForm(forms.ModelForm):
    class Meta:
        #model.py의 모델
        model = Blog 
        fields = ['name', 'email', 'comment']
```


### models
```python
#models.py
from django.db import models

#ModelForm model
class Blog(models.Model):
    name = models.CharField(max_length=255)
    email = models.EmailField()
    comment = models.TextField()
    
    def __str__(self):
    	template = '{0.name} {0.email} {0.comment}'
    	return template.format(self)
```

두 Form 모두 Form 필드를 생성하지만 모델과 관련된 Form을 생성 시 Model Form을 사용하는 것이 더 좋다.

위의 Normal Form은 Model이 없어도 정의해서 사용할 수 있는 반면에 Model Form은 모델을 지정해주어야 한다.

<br>
<br>
<br>


# form.save(), form.save(commit = False)

django에서 form을 사용하다 보면 가끔씩 commit = False를 보게 된다.
ModelForm 클래스에는 save 메소드가 save(self, commit = True)의 형태로 내장되어 있는데 이것은 내부적으로 구현되어 있다.

따라서 form.save()를 사용 시 자동적으로 DB에 내용이 저장되고 반영된다.

<br>
## commit(false)를 사용하는 이유
commit = False를 사용하게 되면 데이터베이스에 바로 저장하지 않는다.
원래 목적은 DB save를 지연시켜 데이터베이스에 중복 save를 방지하는 것이지만, 이것은 보통 DB에 데이터를 저장하기 전에 일련의 작업을 하고 싶을 때 사용한다.

이것을 주로 사용하는 경우는 모델에 모든 필수 필드가 정의되지 않은 ModelForm을 사용하는 경우입니다.

Model에서 일부 Null=False를 비 양식 데이터로 채워야 할 때 주로 사용됩니다.
