### Submission File


You must hand in a pax.Z file to the assignment submission folder on Learning Hub.


```bash
pax -w config/ data/ pcap/ report/ source/ video/ -f <name>-v#.pax
compress -f <name>-v#.pax
```

Hand in the resulting <name>-v#.pax.Z file.
For example, for COMP1234, assignment 3, submission 1, you would do the following:


```bash
pax -w config/ data/ pcap/ report/ source/ video/ -f COMP1234-assign3-v1.pax
compress -f COMP1234-assign3-v1.pax
```

If you need to submit a second version, you would do the following:

```bash
pax -w config/ data/ pcap/ report/ source/ video/ -f  COMP1234-assign3-v2.pax
compress -f COMP1234-assign3-v2.pax
```

---

### Verify Submission File

You should verify that your submission file is correct before uploading it to Learning Hub.

- First, copy the file to a new directory

```bash
uncompress <file name>.pax.Z
pax -r < <file name>.pax
	  ^---- This is not a typo
```

Verify that the directory structure and files you intend to submit are present.

---


There is a huge difference between config/ and assign1/config.

MUST BE config/
