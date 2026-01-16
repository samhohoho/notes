## Spring Data configuration class

`LocalContainerEntityManagerFactoryBean`
a factory bean
produces `EntityManagerFactory`
following
JPA standard container
bootstrap contract.

`setPackagesToScan`,
packages
to scan
for entity classes.

```java
@EnableJpaRepositories("com.manning.javapersistence.ch02.repositories")
public class SpringDataConfiguration {
    @Bean
    public DataSource dataSource() {
        DriverManagerDataSource dataSource = new DriverManagerDataSource();
        dataSource.setDriverClassName("com.mysql.cj.jdbc.Driver");
        dataSource.setUrl(
            "jdbc:mysql://localhost:3306/CH02?serverTimezone=UTC");
        dataSource.setUsername("root");
        dataSource.setPassword("");
        return dataSource;
    }

    @Bean
    public JpaTransactionManager transactionManager(EntityManagerFactory emf) {
        return new JpaTransactionManager(emf);
    }

    @Bean
    public JpaVendorAdapter jpaVendorAdapter() {
        HibernateJpaVendorAdapter jpaVendorAdapter = new
            HibernateJpaVendorAdapter();
        jpaVendorAdapter.setDatabase(Database.MYSQL);
        jpaVendorAdapter.setShowSql(true);
        return jpaVendorAdapter;
    }

    @Bean
    public LocalContainerEntityManagerFactoryBean entityManagerFactory() {
        LocalContainerEntityManagerFactoryBean
            localContainerEntityManagerFactoryBean =
                new LocalContainerEntityManagerFactoryBean();
        localContainerEntityManagerFactoryBean.setDataSource(dataSource());
        Properties properties = new Properties();
        properties.put("hibernate.hbm2ddl.auto", "create");
        localContainerEntityManagerFactoryBean.
            setJpaProperties(properties);
        localContainerEntityManagerFactoryBean.
            setJpaVendorAdapter(jpaVendorAdapter());
        localContainerEntityManagerFactoryBean.
            setPackagesToScan("com.manning.javapersistence.ch02");
        return localContainerEntityManagerFactoryBean;
    }
}
```