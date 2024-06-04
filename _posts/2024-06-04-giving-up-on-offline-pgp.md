---
permalink: '/blog/giving-up-on-offline-pgp'
title: 'giving up on offline pgp keys'
---
In 2018, I revamped my PGP keys, deprecating old keys that were created when I was a baby sysadmin, and replacing them with a ~new fancy offline master key with expiring subkeys~. This meant that my keys were on a Raspberry Pi that had its network interfaces disabled. I only ever used the built-in serial terminal to interface with the master key - it was otherwise fully airgapped and more secure than anything else has ever been in my life.

Well, my subkeys expired in 2020, and because it was such a PITA to fix, I just let them expire. To be fair, there was a pandemic going on. But I also never got around to it in any of the four years that followed.

In that time, I gave up on PGP in general. I read [The PGP Problem](https://www.latacora.com/blog/2019/07/16/the-pgp-problem/) and [Filippo's blog post](https://words.filippo.io/giving-up-on-long-term-pgp/). [SKS died](https://gist.github.com/rjhansen/67ab921ffb4084c865b3618d6955275f), and we had to [kill the keyserver I helped run](https://github.com/ocf/puppet/issues/816). So, I didn't have much incentive to preserve my PGP keys.

But, eventually I realized that they can be useful. PGP keys are still frequently used for package signing or verification of git commits. I'd like to join [dn42](https://dn42.dev), and they use PGP keys to prevent AS or IP space takeovers instead of relying on LOAs (lol).[^dn42-keys] Like it or not, in many spaces, PGP is the established default.

So I've realized that slightly less secure keys are probably better than no keys at all. Rather than having to find my UART adapter, I've given up on the Pi setup. To this end, my master key is no longer offline - it's on the laptop I'm using to publish this post, protected by a passphrase. This puts it in approximately the same class of security as my bank credentials, all the infra I have access to, my email account and all my backups, etc. So I think it's probably fine.

I've updated my keys to include the email I use these days. I also added a non-expired encryption subkey, in case you really need to send me something PGP-encrypted for whatever reason. I don't have an active signing or authentication key, as I don't use these at the moment.

My keys are available on [keys.openpgp.org](https://keys.openpgp.org/search?q=F1DA0D0FD84CDA4C6FE052E365F6C6C95459F55E), or you can just download it from this website - [cg505.com/key.asc](/key.asc). The fingerprint is `F1DA0D0FD84CDA4C6FE052E365F6C6C95459F55E`. I will not be using WKD as [I'd like to be able to read my email](https://matduggan.com/why-cant-my-mom-email-me/) - this may require me to remove the key from keys.opepgp.org if I have problems in the future. If you want to sign my key, go ahead, I guess. I'm not going to be making an effort to get into the strong set or anything like that.

If you want to reach me securely, please don't send me an encrypted email. Message me on Signal, where my username is `cg5.05`. See you around!

<p class="signoff">&mdash; cg505</p>

[^dn42-keys]:  You _can_ also use SSH keys to sign dn42 changes, but this feels like a misuse of SSH keys. I want my SSH keys to do one thing (authenticate me to SSH servers) and nothing else. I'd rather use PGP keys since they're at least designed to be general-purpose, for better or worse. This argument gernalizes to all use of SSH for signing git commits.
