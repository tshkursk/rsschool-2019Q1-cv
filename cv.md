#Personal CV - Tatsiana Peratrukhina

* Tatsiana Peratrukhina

---
* **Email:** *tanya.shkurskaya@gmail.com;* **Skype:** *tanya.shkurskaya*

---
* I joined RS school to get acquainted with Front-end development:
    * understand how web ui is being created;
    * which specific features/underwater rocks are;
    * make sure if I could deal with such work and it is a real interest for me;
    * get some valuable feedback on my practical tasks.


---
* Skills: Java in test automation (Java 8+, Selenium WD, Appium, Gradle/Maven, Spring, JUnit, JBehave, Rest-Assured), Jenkins

---
* Latest code examples:  
  
> Category.java  
  
```java
    @JsonIgnoreProperties(ignoreUnknown=true)
    public class Category implements Serializable {

    private static final long serialVersionUID = 4766147898958329545L;

    private String id;

    private String name;

    // Known issue here - typo in a field name
    //TODO: Update when API fixed
    private String descripition;

    @JsonInclude(JsonInclude.Include.NON_NULL) 
    private List<Category> subcategories;

    @JsonProperty("subcategories_count")
    @JsonInclude(JsonInclude.Include.NON_NULL)
    private Integer subcategoriesCount;

    public String getId() {
        return id;
    }

    public void setId(String id) {
        this.id = id;
    }
    ...(the rest setters/getters of a POJO)
}
```
> CategoryImportTests.java  
  
```java
    @Test
    @DisplayName(SINGLE_TOP_LEVEL_CATEGORY_IMPORT_TEST_NAME)
    void testTopLevelCategoryImport() throws IOException {

        RootCategory rootCategory = JsonUtils.toObject(
                getClass().getResourceAsStream(FAKE_CATEGORIES_JSON_FILENAME), RootCategory.class);
        Category topLevelCategory = rootCategory.getSubcategories().get(0);
        String id = prepareEmptyTopLevelCategory(topLevelCategory, SINGLE_TOP_LEVEL_CATEGORY_IMPORT_TEST_NAME);
        stubTBResponseAndTriggerImport(rootCategory);

        ValidatableResponse response = given().get(DAL_CATEGORIES_PATH + id).then();
        assertAll(() -> {
            response.assertThat().spec(baseCheckForCategory);
            assertAll(
                    () -> response.assertThat().body(EXTERNAL_ID, equalTo(id)),
                    () -> response.assertThat().body(DAL_NAME_FIELD, equalTo(topLevelCategory.getName())),
                    () -> response.assertThat().body(DAL_DESCRIPTION_FIELD,
                            equalTo(topLevelCategory.getDescripition())),
                    () -> response.assertThat().body(IMAGE, notNullValue()),
                    () -> response.assertThat().body(CATALOG_ID, equalTo(0)),
                    () -> response.assertThat().body(PARENT_CATEGORY_ID, equalTo(0)),
                    () -> response.assertThat().body(IS_ROOT, equalTo(true))
            );
        });
    }
```

---
* Senior Software Test Automation Engineer, EPAM 3+ years
    * Finished EPAM FT CDP program, tried myself as a mentor in it;
    * Finished Spring Core/Advanced Java EPAM courses;
    * Finished Java D1 EPAM courses.

---
* Belarusian State University, Radiophysics and Computer Technologies

---
* B1+

---