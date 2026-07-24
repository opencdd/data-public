# frozen_string_literal: true

# data-public Rakefile — OceanRunner sample build only.
# Full IEC data pipeline lives in opencdd/data-private.

require "json"

DATA_DIR = File.expand_path(File.join(__dir__, "data")).freeze

def cdd_config
  @cdd_config ||= begin
    path = File.join(__dir__, "cdd.config.yml")
    defaults = { "models_ts_dir" => "../opencdd-ts", "opencdd_ruby_dir" => "../opencdd-ruby" }
    if File.file?(path)
      require "yaml"
      parsed = YAML.safe_load(File.read(path)) || {}
      defaults.merge(parsed)
    else
      defaults
    end
  end
end

def models_ts_dir
  ENV.fetch("CDD_MODELS_TS_DIR", File.expand_path(cdd_config["models_ts_dir"], __dir__))
end

# ── TS codegen ──────────────────────────────────────────────────
desc "Regenerate TypeScript registry files for opencdd-ts (@opencdd/models)"
task :generate_ts do
  require "opencdd"
  dir = models_ts_dir
  unless File.directory?(dir)
    abort "opencdd-ts not found at #{dir}. Set models_ts_dir in cdd.config.yml or CDD_MODELS_TS_DIR env."
  end
  Opencdd::Codegen::Ts.generate_all(dir)
end

namespace :browser do
  desc "Build the OceanRunner sample fixture (CDDAL → JSON)"
  task :sample do
    require "opencdd"
    src = File.expand_path("reference-docs/examples/oceanrunner.cddal", __dir__)
    db = Opencdd::Cddal.parse_file(src)
    json = Opencdd::Exporters::Json.new.to_json(db)
    out_dir = File.join(DATA_DIR, "oceanrunner")
    FileUtils.mkdir_p(out_dir)
    File.write(File.join(out_dir, "database.json"), json)
    puts "Wrote oceanrunner → #{out_dir}"
  end
end

task default: "browser:sample"
