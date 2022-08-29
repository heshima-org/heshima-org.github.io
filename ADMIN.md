# Operations

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

Should return

```txt
;heshima.org.uk.                        IN      A
heshima.org.uk.         5895    IN      A       185.199.111.153
heshima.org.uk.         5895    IN      A       185.199.110.153
heshima.org.uk.         5895    IN      A       185.199.108.153
heshima.org.uk.         5895    IN      A       185.199.109.153
```

And confirm the `www` subdomain

    dig www.heshima.org.uk +nostats +nocomments +nocmd

```txt
;www.heshima.org.uk.            IN      A
www.heshima.org.uk.     85823   IN      CNAME   heshima-org.github.io.
heshima-org.github.io.  3023    IN      A       185.199.108.153
heshima-org.github.io.  3023    IN      A       185.199.110.153
heshima-org.github.io.  3023    IN      A       185.199.109.153
heshima-org.github.io.  3023    IN      A       185.199.111.153
```

Check that all the following work OK and redirect to <https://heshima.org.uk>.

- <http://heshima.org.uk>
- <https://heshima.org.uk>
- <http://www.heshima.org.uk>
- <https://www.heshima.org.uk>

If the <https://www.heshima.org.uk> certificate is not valid because it is not
generated for the `www` subdomain, then you can remove and re-add the domain in
the GitHub settings for pages. If this is done after the `CNAME` is set up for the
`www` subdomain then the certificate should be created to support both the
`heshima.org.uk` apex domain and the `www.heshima.org.uk` subdomain.

This can be verified with

    echo |
      openssl s_client -showcerts -servername www.heshima.org.uk -connect www.heshima.org.uk:443 2>/dev/null |
      openssl x509 -inform pem -noout -text | grep heshima

which should return

```txt
  Subject: CN=heshima.org.uk
    DNS:heshima.org.uk, DNS:www.heshima.org.uk
```
