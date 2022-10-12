-----------------------------------------------------------------------
  Example setup.py file      | from setuptools import find_packages, setup
                             |
                             | with open('README.md', 'r') as f:
                             |     long_description = f.read()
                             |
                             | setup(
                             |     name='pgbackup',
                             |     version='0.1.0',
                             |     author='William Acevedo',
                             |     author_email='william.acevedo@gmail.com',
                             |     description='A utility for backing up PostgreSQL databases',
                             |     long_description=long_description,
                             |     long_description_content_type='text/markdown',
                             |     url='https://github.com/linuxacademy/pgbackup',
                             |     packages=find_packages('src'),
                             |     package_dir={'': 'src'},
                             |     install_requires=['boto3'],
                             |     python_requires='>=3.10.6',
                             |     entry_points={
                             |         'console_scripts': [
                             |             'pgbackup=pgbackup.cli:main'
                             |             ],
                             |         }
                             | )
                             |
  command used to build      | python setup.py bdist_wheel
  package                    |
                             |
  Install package within     | pip install --user -e .
  package top level directory|
                             |
                             |
                             |
                             |
                             |
                             |
                             |
                             |
                             |
                             |
                             |
                             |
                             |
                             |
                             |
                             |
                             |
                             |
                             |
                             |
                             |
                             |
                             |
                             |
                             |
                             |
                             |
                             |
                             |
                             |
                             |
                             |
                             |
                             |
                             |
                             |
                             |
                             |
                             |
                             |
                             |
                             |
                             |
                             |
                             |
                             |
                             |
                             |
                             |
                             |
                             |
                             |
                             |
                             |
                             |
                             |
                             |
                             |
                             |
                             |
                             |
                             |
                             |
                             |
                             |
                             |
                             |
                             |
                             |
                             |
                             |
                             |
                             |
                             |
                             |
                             |
                             |
                             |
                             |
                             |
                             |
                             |
                             |
                             |
                             |
                             |
                             |
                             |
                             |
                             |
                             |
                             |
                             |
                             |
                             |
