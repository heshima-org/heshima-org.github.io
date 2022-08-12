# heshima-org.github.io

Heshima Web Site

## Setting up domain

In GitHub project settings Pages ticket **Enforce HTTPS**.

Follow guidance on [Managing a custom domain for your GitHub Pages
site](https://docs.github.com/en/pages/configuring-a-custom-domain-for-your-github-pages-site/managing-a-custom-domain-for-your-github-pages-site#setting-up-a-subdomain).

Login <https://controlpanel.easyspace.com/> and navigate to <heshima.org.uk>
management. Make sure nameservers point to default nameservers, click **Update
to default nameservers** if they don't and wait a little while.

Click on **Manage DNS** tab and set A records for `heshima.org.uk` to:

```txt
185.199.108.153
185.199.109.153
185.199.110.153
185.199.111.153
```

Create a `CNAME` record from `www.heshima.org.uk` to `heshima-org.github.io`.

Confirm with

    dig heshima.org.uk +nostats +nocomments +nocmd
    dig www.heshima.org.uk +nostats +nocomments +nocmd
