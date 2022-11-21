---
# Feel free to add content and custom Front Matter to this file.
# To modify the layout, see https://jekyllrb.com/docs/themes/#overriding-theme-defaults
layout: page 
---

* [Migrating a domain between AWS accounts](/_posts/2022-11-09-migrate-domain-between-aws-accounts)
* [Using IAM to manage EKS authentication](_posts/2022-11-21-Using_IAM_to_manage_EKS_authentication)
{% for tag in site.tags %}
=={{ tag[0] }}==
  {% for post in tag[1] %}
   [{{ post.title }}]({{ post.url }})
  {% endfor %}
{% endfor %}
