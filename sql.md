SQL injection vulnerability exists in ibos Office OA v 4.5.5

official website:http://www.ibos.com.cn/

version:4.5.5

Function point: Integrated office = "Recruitment management =" Status selection


![WPS图片(1)](https://github.com/netman2023/cve/assets/141479433/00b751c3-b16d-49dc-ace7-fa548d7238f7)

Route: r=recruit/resume/edit&op=status

The injection parameter resumeid exists

Successfully burst the database name by reporting an error injection

![WPS图片(2)](https://github.com/netman2023/cve/assets/141479433/afe3157e-6847-415e-bf74-033e5217a112)

By finding the method actionEdit(), we get two parameters, an op parameter that controls branch selection, and a second resumeid, which is an injected parameter.

![WPS图片(3)](https://github.com/netman2023/cve/assets/141479433/4138114f-eba9-4a1a-b181-559c64c771f2)

Op! =default So go else and call the status() method under this controller

![WPS图片(4)](https://github.com/netman2023/cve/assets/141479433/aec99be4-f1c1-41ad-9ee9-2f0936572f56)
SQL statements are executed using the updateAll wrapper function under the model layer

![WPS图片(5)](https://github.com/netman2023/cve/assets/141479433/84005d29-0c03-4ff9-8fda-8e9a1dc17987)

![WPS图片(6)](https://github.com/netman2023/cve/assets/141479433/75efc14c-2b37-48f0-8b87-e0ac93d19972)
UpdateAll

![WPS图片(7)](https://github.com/netman2023/cve/assets/141479433/fca3ff58-8c99-4b73-ba38-679eae5a3ed4)
