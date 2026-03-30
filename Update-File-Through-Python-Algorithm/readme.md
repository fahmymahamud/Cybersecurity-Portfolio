# **Update a file through a Python algorithm**

## 📌 Project Description
This repository features a Python-driven solution for maintaining network security within a healthcare environment. The project demonstrates the creation of an automated algorithm to manage access control for restricted subnetworks, ensuring that sensitive patient data is only accessible to authorized IP addresses.

At the organization, access to restricted content is controlled with an **allow list** of IP addresses.  
- The file `allow_list.txt` contains these IP addresses.  
- A separate **remove list** identifies IP addresses that should no longer have access.  

I created a Python algorithm to **automate updating** the `allow_list.txt` file by removing IP addresses found in the remove list.


### 🛠️ Technical Workflow & Skill Showcase
I developed a streamlined algorithm to automate the "allow list" update process, replacing manual administrative tasks with efficient, repeatable code. The workflow highlights proficiency in file handling, data structure manipulation, and defensive programming:

**File Ingestion & Context Management**: Utilized Python’s with open() statement to securely access the allow_list.txt file, ensuring robust file handling and data integrity during the read process.

**Data Transformation**: Parsed raw string data from the security manifest and converted it into a dynamic List of IP addresses, enabling efficient iteration and programmatic filtering.

**Algorithmic Removal Logic**: Implemented a controlled loop to iterate through a targeted remove_list. The algorithm cross-references every entry and uses Python’s .remove() method to purge unauthorized IP addresses in real-time.

**Serialization & Reformatting**: Transformed the cleaned list back into a standardized string format using the .join() method, ensuring the data remains compatible with the organization's existing security infrastructure.

**Secure Data Persistence**: Automated the final update by writing the revised, authorized-only list back into the allow_list.txt file, effectively closing the "window of vulnerability" for revoked access points.

---

## ⚙️ Steps in the Algorithm

### 1. Open the Allow List File
```python
import_file = "allow_list.txt"

with open(import_file, "r") as file:
    ip_addresses = file.read()

- `open(import_file, "r")` opens the file in **read mode**.  
- The `with` statement ensures the file is closed automatically after use.  
- The contents are read into the variable `ip_addresses`.
```
---

### 2. Read File Contents
```python
ip_addresses = file.read()
```
- `.read()` converts the file contents into a **string**.  
- This allows further manipulation of the IP addresses.

---

### 3. Convert String into a List
```python
ip_addresses = ip_addresses.split()
```
- `.split()` converts the string into a **list** of IP addresses.  
- Each IP address becomes an element in the list, making removal easier.

---

### 4. Iterate Through the Remove List
```python
for element in remove_list:
    if element in ip_addresses:
        ip_addresses.remove(element)
```
- A `for` loop iterates through each IP in `remove_list`.  
- If the IP exists in `ip_addresses`, it is removed using `.remove()`.

---

### 5. Update the File with Revised List
```python
ip_addresses = "\n".join(ip_addresses)

with open(import_file, "w") as file:
    file.write(ip_addresses)
```
- `.join()` converts the list back into a **string**, separating each IP with a newline.  
- The file is reopened in **write mode ("w")**.  
- `.write()` replaces the file contents with the updated allow list.

---

## 📂 Example File Workflow
- **Input:**  
  - `allow_list.txt` → contains approved IPs  
  - `remove_list` → contains IPs to revoke  

- **Output:**  
  - Updated `allow_list.txt` with revoked IPs removed  

---

## 🔄 Algorithm Flowchart

```

 ┌───────────────────────┐
 │   Start Algorithm     │
 └───────────┬───────────┘
             │
             ▼
 ┌───────────────────────┐
 │ Open "allow_list.txt" │
 │   (read mode "r")     │
 └───────────┬───────────┘
             │
             ▼
 ┌───────────────────────┐
 │ Read file contents    │
 │   → string format     │
 └───────────┬───────────┘
             │
             ▼
 ┌───────────────────────┐
 │ Convert string to     │
 │   list of IPs         │
 └───────────┬───────────┘
             │
             ▼
 ┌───────────────────────┐
 │ Iterate through        │
 │   remove_list          │
 └───────────┬───────────┘
             │
             ▼
 ┌───────────────────────┐
 │ If IP in allow_list   │
 │   → remove()          │
 └───────────┬───────────┘
             │
             ▼
 ┌───────────────────────┐
 │ Convert list back to  │
 │   string with .join() │
 └───────────┬───────────┘
             │
             ▼
 ┌───────────────────────┐
 │ Write updated string  │
 │   to "allow_list.txt" │
 │   (write mode "w")    │
 └───────────┬───────────┘
             │
             ▼
 ┌───────────────────────┐
 │   End Algorithm       │
 └───────────────────────┘

```
---

## ✅ Summary
This algorithm:
1. Opens and reads the `allow_list.txt` file.  
2. Converts its contents into a list of IP addresses.  
3. Iterates through the `remove_list` and removes matching IPs.  
4. Converts the updated list back into a string.  
5. Writes the revised list back into `allow_list.txt`.  

As a result, restricted content is no longer accessible to IP addresses that were removed from the allow list.

---

## 🚀 Future Improvements
- Add logging to track removed IPs.  
- Implement error handling for missing files.  
- Extend functionality to handle duplicate IPs.  
- Integrate with a database or API for dynamic updates.  
