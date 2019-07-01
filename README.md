# hello-world
love and peace

	@Test
	public void test() {
		String resource = "beans.xml";
		InputStream inputStream;
		try {
			inputStream = Resources.getResourceAsStream(resource);
			SqlSessionFactory sqlSessionFactory = new SqlSessionFactoryBuilder().build(inputStream);
			SqlSession session = sqlSessionFactory.openSession();

			UserDao userDao = session.getMapper(UserDao.class);
			List<User> list = userDao.showAll();
			for (User user : list) {
				System.out.println(
						user.getId() + user.getEmail() + user.getIdCard() + user.getPassword() + user.getPhoneNumber()
								+ user.getRealName() + user.getSex() + user.getUser_status() + user.getUserName());
			}
			session.close();

		} catch (IOException e) {
			e.printStackTrace();
		}
	}
