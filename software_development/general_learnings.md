# General Learnings from Backend Developments

1.  For FastAPI backend, to implement system level environment configuration, use _pydantic-settings_ for environment variables.
2.  In pydantic_settings, use BaseSettings class, and SettingsConfigDict class. Below is a sample code:

    ```
    from pydantic_settings import BaseSettings, SettingsConfigDict
    class Settings(BaseSettings):

                    project_name: str
                    database_url: str

                    model_config = SettingsConfigDict(
                        env_file=".env",
                        env_file_encoding="utf-8"
                    )

                    def __init__(self, **data):
                        super().__init__(**data)

                settings = Settings()
    ```
